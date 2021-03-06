---
title: "Planification de l’intégration d’Azure Stack à un pare-feu pour les systèmes intégrés Azure Stack | Microsoft Docs"
description: "Décrit les considérations relatives à l’intégration d’Azure Stack à un pare-feu pour les déploiements d’Azure Stack à plusieurs nœuds connectés à Azure."
services: azure-stack
documentationcenter: 
author: jeffgilb
manager: femila
editor: 
ms.assetid: 
ms.service: azure-stack
ms.workload: na
pms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 02/01/2018
ms.author: jeffgilb
ms.reviewer: wfayed
ms.openlocfilehash: 919618c0779d47f0add02d5e7d3ab9ab4b5bdd10
ms.sourcegitcommit: 059dae3d8a0e716adc95ad2296843a45745a415d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="azure-stack-firewall-integration"></a>Intégration d’Azure Stack à un pare-feu
Nous vous recommandons d’utiliser un dispositif de pare-feu pour sécuriser Azure Stack. Bien que les pare-feu puissent être utiles en cas d’attaques par déni de service distribué (DDOS), de détection des intrusions et d’inspection du contenu, ils peuvent également constituer un goulot d’étranglement au niveau du débit des services de stockage Azure comme les objets blob, les tables et les files d’attente.

Selon le modèle d’identité Azure AD (Azure Active Directory) ou Windows Server AD FS (Active Directory Federation Services), vous devrez peut-être publier le point de terminaison AD FS. Si un mode de déploiement déconnecté est utilisé, vous devez publier le point de terminaison AD FS. Pour plus d’informations, consultez [l’article sur l’identité de l’intégration au centre de données](azure-stack-integrate-identity.md).

Les points de terminaison Azure Resource Manager (administrateur), portail administrateur et Key Vault (administrateur) ne nécessitent aucune publication externe. Par exemple, en tant que fournisseur de services, vous souhaitez peut-être limiter la surface de l’attaque et administrer uniquement Azure Stack à partir de votre réseau et non à partir d’Internet.

Pour les entreprises, le réseau externe peut être le réseau d’entreprise existant. Dans un tel scénario, vous devez publier ces points de terminaison pour exécuter Azure Stack à partir du réseau d’entreprise.

### <a name="network-address-translation"></a>Traduction d’adresses réseau
La traduction d’adresses réseau (NAT, Network Address Translation) est la méthode recommandée pour autoriser la machine virtuelle de déploiement (DVM, Deployment Virtual Machine) à accéder, d’une part, aux ressources externes et à Internet durant le déploiement et, d’autre part, aux machines virtuelles ERCS (Emergency Recovery Console) ou au PEP (Privileged End Point) durant l’inscription et le dépannage.

Vous pouvez également utiliser NAT à la place des adresses IP publiques sur le réseau externe ou des adresses IP virtuelles publiques. Toutefois, ceci n’est pas recommandé car NAT limite l’expérience utilisateur du locataire et accroît la complexité. Les deux options sont les suivantes : NAT 1:1, qui nécessite toujours une adresse IP publique par adresse IP d’utilisateur sur le pool ; ou NAT many:1, qui nécessite une règle NAT pour chaque adresse IP virtuelle d’utilisateur contenant les associations à tous les ports qu’un utilisateur peut utiliser.

L’utilisation de NAT pour une adresse IP virtuelle publique présente des inconvénients. En voici quelques-uns :
- NAT ajoute une surcharge lors de la gestion des règles de pare-feu car les utilisateurs contrôlent leurs propres points de terminaison et leurs propres règles de publication dans la pile de mise en réseau logicielle (SDN). Les utilisateurs doivent contacter l’opérateur Azure Stack pour que leurs adresses IP virtuelles soient publiées et pour mettre à jour la liste des ports.
- Bien que l’utilisation de NAT limite l’expérience de l’utilisateur, elle donne à l’opérateur un contrôle total sur les demandes de publication.
- Pour les scénarios de cloud hybride avec Azure, tenez compte du fait qu’Azure ne prend pas en charge la configuration d’un tunnel VPN vers un point de terminaison à l’aide de NAT.

### <a name="ssl-decryption"></a>Déchiffrement SSL
Actuellement, il est recommandé de désactiver le déchiffrement de SSL pour tout le trafic Azure Stack. S’il venait à être pris en charge dans les futures mises à jour, nous fournirions des conseils sur la façon d’activer le déchiffrement SSL pour Azure Stack.

## <a name="edge-firewall-scenario"></a>Scénario de pare-feu de périmètre
Dans un déploiement de périphérie, Azure Stack est déployé directement derrière le pare-feu ou le routeur de périphérie. Dans ces scénarios, le pare-feu peut se trouver au-dessus de la frontière ou jouer le rôle d’appareil frontière s’il prend en charge ECMP (Equal Cost Multi Path) avec BGP ou le routage statique.

En règle générale, les adresses IP routables publiques sont spécifiées pour le pool d’adresses IP virtuelles publiques à partir du réseau externe au moment du déploiement. Dans un scénario de périphérie, il n’est pas recommandé d’utiliser des adresses IP routables publiques sur un autre réseau pour des raisons de sécurité. Ce scénario permet à un utilisateur de bénéficier d’une expérience cloud auto-contrôlée complète, comme dans un cloud public tel qu’Azure.  

![Exemple de pare-feu de périphérie Azure Stack](.\media\azure-stack-firewall\edge-firewall-scenario.png)

## <a name="enterprise-intranet-or-perimeter-network-firewall-scenario"></a>Scénario de pare-feu réseau de périmètre ou intranet d’entreprise
Dans un déploiement sur un réseau de périmètre ou intranet d’entreprise, Azure Stack est déployé sur un pare-feu multizone ou entre le pare-feu de périphérie et le pare-feu de réseau d’entreprise interne. Le trafic est ensuite distribué entre le réseau de périmètre sécurisé (ou DMZ) et les zones non sécurisées, comme décrit ci-dessous :

- **Zone sécurisée** : Il s’agit du réseau interne qui utilise des adresses IP routables de l’entreprise ou internes. Le réseau sécurisé peut être divisé et avoir un accès sortant à internet par le biais de NAT sur le pare-feu. Vous pouvez généralement y accéder à partir de n’importe quel emplacement à l’intérieur de votre centre de données par le biais du réseau interne. Tous les réseaux Azure Stack doivent résider dans la zone sécurisée, à l’exception du pool d’adresses IP virtuelles publiques du réseau externe.
- **Zone du périmètre**. Les applications externes ou accessibles sur Internet comme les serveurs web sont généralement déployées sur le réseau de périmètre. Celui-ci est habituellement monitoré par un pare-feu pour éviter les attaques de type DDoS et les intrusions (piratage), mais il autorise également le trafic entrant spécifié à partir d’internet. Seul le pool d’adresses IP virtuelles publiques de réseau externe d’Azure Stack doit résider dans la zone DMZ.
- **Zone non sécurisée**. Il s’agit du réseau externe (Internet). Il **n’est pas** recommandé de déployer Azure Stack dans la zone non sécurisée.

![Exemple de réseau de périmètre Azure Stack](.\media\azure-stack-firewall\perimeter-network-scenario.png)

## <a name="learn-more"></a>En savoir plus
Découvrez plus en détail [les ports et les protocoles utilisés par les points de terminaison Azure Stack](azure-stack-integrate-endpoints.md).

## <a name="next-steps"></a>étapes suivantes
[Exigences relatives à l’infrastructure à clé publique d’Azure Stack](azure-stack-pki-certs.md)


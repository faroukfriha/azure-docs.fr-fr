---
title: "Didacticiel : Intégration d’Azure Active Directory à ADP Federated SSO | Microsoft Docs"
description: "Découvrez comment configurer l’authentification unique entre Azure Active Directory et ADP Federated SSO."
services: active-directory
documentationCenter: na
author: jeevansd
manager: femila
ms.reviewer: joflore
ms.assetid: 7be5331b-0481-48f7-9d6b-619dfec657e1
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 02/02/2018
ms.author: jeedes
ms.openlocfilehash: ad12dfd525afe1bde7026535dceb25556abf0a96
ms.sourcegitcommit: fbba5027fa76674b64294f47baef85b669de04b7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2018
---
# <a name="tutorial-azure-active-directory-integration-with-adp-federated-sso"></a>Didacticiel : Intégration d’Azure Active Directory à ADP Federated SSO

Dans ce didacticiel, vous allez apprendre à intégrer ADP Federated SSO à Azure Active Directory (Azure AD).

L’intégration d’ADP Federated SSO à Azure AD vous offre les avantages suivants :

- Dans Azure AD, vous pouvez contrôler qui a accès à ADP Federated SSO.
- Vous pouvez autoriser les utilisateurs à se connecter automatiquement à ADP Federated SSO (par le biais de l’authentification unique) avec leur compte Azure AD.
- Vous pouvez gérer vos comptes dans un emplacement central : le portail Azure

Pour en savoir plus sur l’intégration des applications SaaS avec Azure AD, consultez [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](active-directory-appssoaccess-whatis.md).

## <a name="prerequisites"></a>configuration requise

Pour configurer l’intégration d’Azure AD à ADP Federated SSO, vous avez besoin des éléments suivants :

- Un abonnement Azure AD
- Un abonnement ADP Federated SSO pour lequel l’authentification unique est activée

> [!NOTE]
> Pour tester les étapes de ce didacticiel, nous déconseillons l’utilisation d’un environnement de production.

Vous devez en outre suivre les recommandations ci-dessous :

- N’utilisez pas votre environnement de production, sauf si cela est nécessaire.
- Si vous n’avez pas d’environnement d’essai Azure AD, vous pouvez [obtenir un essai d’un mois](https://azure.microsoft.com/pricing/free-trial/).

## <a name="scenario-description"></a>Description du scénario
Dans ce didacticiel, vous testez l’authentification unique Azure AD dans un environnement de test. Le scénario décrit dans ce didacticiel se compose des deux sections principales suivantes :

1. Ajout d’ADP Federated SSO à partir de la galerie
2. Configuration et test de l’authentification unique Azure AD

## <a name="adding-adp-federated-sso-from-the-gallery"></a>Ajout d’ADP Federated SSO à partir de la galerie
Pour configurer l’intégration d’ADP Federated SSO à Azure AD, vous devez ajouter ADP Federated SSO à partir de la galerie à votre liste d’applications SaaS gérées.

**Pour ajouter ADP Federated SSO à partir de la galerie, effectuez les étapes suivantes :**

1.  Ouvrez une session en tant qu’administrateur sur votre environnement de fournisseur d’identité Microsoft Azure.

2. Dans le volet de navigation gauche du **[portail Azure](https://portal.azure.com)**, cliquez sur l’icône **Azure Active Directory**. 

    ![Bouton Azure Active Directory][1]

3. Accédez à **Applications d’entreprise**. Accédez ensuite à **Toutes les applications**.

    ![Panneau Applications d’entreprise][2]
    
4. Pour ajouter l’application, cliquez sur le bouton **Nouvelle application** en haut de la boîte de dialogue.

    ![Bouton Nouvelle application][3]

5. Dans la zone de recherche, tapez **ADP Federated SSO**, sélectionnez **ADP Federated SSO** dans le volet de résultats, puis cliquez sur le bouton **Ajouter** pour ajouter l’application.

    ![ADP Federated SSO dans la liste des résultats](./media/active-directory-saas-adpfederatedsso-tutorial/tutorial_adpfederatedsso_addfromgallery.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>Configurer et tester l’authentification unique Azure AD

Dans cette section, vous allez configurer et tester l’authentification unique Azure AD auprès d’ADP Federated SSO avec un utilisateur de test appelé « Britta Simon ».

Pour que l’authentification unique fonctionne, Azure AD doit savoir qui est l’utilisateur ADP Federated SSO équivalent dans Azure AD. En d’autres termes, une relation entre un utilisateur Azure AD et un utilisateur ADP Federated SSO associé doit être établie.

Dans ADP Federated SSO, assignez la valeur de **nom d’utilisateur** dans Azure AD comme valeur de **nom d’utilisateur** pour établir la relation.

Pour configurer et tester l’authentification unique Azure AD avec ADP Federated SSO, vous devez suivre les indications des sections suivantes :

1. **[Configurer l’authentification unique Azure AD](#configure-azure-ad-single-sign-on)** pour permettre à vos utilisateurs d’utiliser cette fonctionnalité.
2. **[Créer un utilisateur de test Azure AD](#create-an-azure-ad-test-user)** pour tester l’authentification unique Azure AD avec Britta Simon.
3. **[Créer un utilisateur de test ADP Federated SSO](#create-an-adp-federated-sso-test-user)** pour avoir un équivalent de Britta Simon dans ADP Federated SSO lié à la représentation Azure AD de l’utilisateur.
4. **[Affecter l’utilisateur de test Azure AD](#assign-the-azure-ad-test-user)** pour permettre à Britta Simon d’utiliser l’authentification unique Azure AD.
5. **[Tester l’authentification unique](#test-single-sign-on)** : pour vérifier si la configuration fonctionne.

### <a name="configure-azure-ad-single-sign-on"></a>Configurer l’authentification unique Azure AD

Dans cette section, vous allez activer l’authentification unique Azure AD dans le portail Azure et configurer l’authentification unique dans votre application ADP Federated SSO.

**Pour configurer l’authentification unique Azure AD avec ADP Federated SSO, effectuez les étapes suivantes :**

1. Dans le portail Azure, dans la page d’intégration de l’application **ADP Federated SSO**, cliquez sur **l’onglet Propriétés** et effectuez les étapes suivantes : 

    ![Propriétés de l’authentification unique](./media/active-directory-saas-adpfederatedsso-tutorial/tutorial_adpfederatedsso_prop.png)

    a. Définissez le champ **Activé pour que les utilisateurs se connectent** sur **Oui**.

    b. Copiez **l’URL d’accès utilisateur** et collez-la dans la **section Configurer l’URL d’authentification**, comme expliqué plus loin dans le didacticiel.

    c. Définissez le champs **Affectation de l’utilisateur obligatoire** sur **Oui**.

    d. Définissez le champ **Visible par les utilisateurs** sur **Non**.

2. Cliquez sur **Authentification unique** dans la page d’intégration de l’application **ADP Federated SSO**.

    ![Lien Configurer l’authentification unique][4]

3. Dans la boîte de dialogue **Authentification unique**, pour le **Mode**, sélectionnez **Authentification basée sur SAML** pour activer l’authentification unique.
 
    ![Boîte de dialogue Authentification unique](./media/active-directory-saas-adpfederatedsso-tutorial/tutorial_adpfederatedsso_samlbase.png)

4. Dans la section **Domaine et URL ADP Federated SSO**, effectuez les étapes suivantes :

    ![Informations d’authentification unique dans Domaine et URL ADP Federated SSO](./media/active-directory-saas-adpfederatedsso-tutorial/tutorial_adpfederatedsso_url.png)

    Dans la zone de texte **Identificateur**, tapez une URL : `https://fed.adp.com/` 
    
5. L’application ADP Federated SSO s’attend à recevoir les assertions SAML dans un format spécifique, ce qui vous oblige à ajouter des mappages d’attributs personnalisés à votre configuration Attributs du jeton SAML. La capture d’écran suivante montre un exemple : Le nom de la revendication sera toujours **« PersonImmutableID »** et sa valeur mappée à **employeeid**. 

    Ici, le mappage utilisateur d’Azure AD à ADP Federated SSO est effectué avec **employeeid**, mais vous pouvez le mapper à une valeur différente basée sur les paramètres de votre application. Ainsi, contactez d’abord [l’équipe du support ADP](https://www.adp.com/contact-us/overview.aspx) pour utiliser le bon identificateur d’utilisateur et mapper cette valeur à la revendication **« PersonImmutableID »**.

    ![Configure Single Sign-On](./media/active-directory-saas-adpfederatedsso-tutorial/tutorial_adpfederatedsso_attribute.png)

6. Dans la section **Attributs utilisateur** de la boîte de dialogue **Authentification unique**, configurez l’attribut de jeton SAML comme sur l’image et procédez comme suit :
    
    | Nom de l'attribut | Valeur de l’attribut |
    | ------------------- | -------------------- |    
    | PersonImmutableID | user.employeeid |
    
    a. Cliquez sur **Ajouter un attribut** pour ouvrir la boîte de dialogue **Ajouter un attribut**.

    ![Configure Single Sign-On](./media/active-directory-saas-adpfederatedsso-tutorial/tutorial_attribute_04.png)

    ![Configure Single Sign-On](./media/active-directory-saas-adpfederatedsso-tutorial/tutorial_attribute_05.png)

    b. Dans la zone de texte **Attribut**, indiquez le nom d’attribut pour cette ligne.

    c. Dans la liste **Valeur** , saisissez la valeur d’attribut affichée pour cette ligne.
    
    d. Cliquez sur **OK**.

    > [!NOTE] 
    > Avant de pouvoir configurer votre assertion SAML, vous devez contacter [l’équipe du support ADP](https://www.adp.com/contact-us/overview.aspx) et lui demander d’affecter la valeur d’attribut d’identificateur unique à votre locataire. Vous avez besoin de cette valeur pour configurer la revendication personnalisée pour votre application. 

7. Dans la section **Certificat de signature SAML**, cliquez sur **Métadonnées XML** puis enregistrez le fichier de métadonnées sur votre ordinateur.

    ![Lien de téléchargement du certificat](./media/active-directory-saas-adpfederatedsso-tutorial/tutorial_adpfederatedsso_certificate.png) 

8. Pour configurer l’authentification unique côté **ADP Federated SSO**, vous devez charger le **XML de métadonnées** téléchargé sur le [site web ADP Federated SSO](https://adpfedsso.adp.com/public/login/index.fcc).

> [!NOTE]  
> Ce processus peut prendre quelques jours. 

### <a name="configure-your-adp-services-for-federated-access"></a>Configurer vos services ADP pour un accès fédéré

>[!Important]
> Vous devez assigner à l’application de service ADP les employés qui ont besoin d’un accès fédéré à vos services ADP, puis réassigner les utilisateurs à un service ADP spécifique.
Une fois la confirmation reçue de votre représentant ADP, configurez vos services ADP et assignez/gérez les utilisateurs pour contrôler l’accès utilisateur à un service ADP spécifique.

1. Dans le volet de navigation gauche du **[portail Azure](https://portal.azure.com)**, cliquez sur l’icône **Azure Active Directory**. 

    ![Bouton Azure Active Directory][1]

2. Accédez à **Applications d’entreprise**. Accédez ensuite à **Toutes les applications**.

    ![Panneau Applications d’entreprise][2]
    
3. Pour ajouter l’application, cliquez sur le bouton **Nouvelle application** en haut de la boîte de dialogue.

    ![Bouton Nouvelle application][3]

4. Dans la zone de recherche, tapez **ADP Federated SSO**, sélectionnez **ADP Federated SSO** dans le volet de résultats, puis cliquez sur le bouton **Ajouter** pour ajouter l’application.

    ![ADP Federated SSO dans la liste des résultats](./media/active-directory-saas-adpfederatedsso-tutorial/tutorial_adpfederatedsso_addservicegallery.png)

5. Dans le portail Azure, dans votre page d’intégration de l’application **ADP Federated SSO**, cliquez sur **l’onglet Propriétés** et effectuez les étapes suivantes :  

    ![Propriétés de l’authentification unique liée](./media/active-directory-saas-adpfederatedsso-tutorial/tutorial_adpfederatedsso_linkedproperties.png)

    a.  Définissez le champ **Activé pour que les utilisateurs se connectent** sur **Oui**.

    b.  Définissez le champs **Affectation de l’utilisateur obligatoire** sur **Oui**.

    c.  Définissez le champ **Visible par les utilisateurs** sur **Oui**.

6. Cliquez sur **Authentification unique** dans la page d’intégration de l’application **ADP Federated SSO**.

    ![Lien Configurer l’authentification unique][4]

7. Dans la boîte de dialogue **Authentification unique**, sélectionnez **Mode** comme **Authentification liée** pour lier votre application à **Authentification unique fédérée ADP**.

    ![Authentification unique liée](./media/active-directory-saas-adpfederatedsso-tutorial/tutorial_adpfederatedsso_linked.png)

8. Accédez à la section **Configurer l’URL d’authentification**, puis effectuez les étapes suivantes :

    ![Propriétés de l’authentification unique](./media/active-directory-saas-adpfederatedsso-tutorial/tutorial_adpfederatedsso_linkedsignon.png)
                                                              
    a. Collez **l’URL d’accès utilisateur**, que vous avez copiée à partir de **l’onglet Propriétés** plus haut (à partir de l’application ADP Federated SSO principale).
                                                             
    b. Voici les 5 applications qui prennent en charge différentes **URL d’état de relais**. Vous devez ajouter la valeur **d’URL d’état de relais** appropriée pour une application particulière manuellement à **l’URL d’accès utilisateur**.
    
    * **ADP Workforce Now**
        
        `<User access URL>?Relay State=https://fed.adp.com/saml/fedlanding.html?WFN`

    * **ADP Workforce Now Enhanced Time**
        
        `<User access URL>?Relay State=https://fed.adp.com/saml/fedlanding.html?EETDC2`
    
    * **ADP Vantage HCM**
        
        `<User access URL>?Relay State=https://fed.adp.com/saml/fedlanding.html?ADPVANTAGE`

    * **ADP Enterprise HR**

        `<User access URL>?Relay State=https://fed.adp.com/saml/fedlanding.html?PORTAL`

    * **MyADP**

        `<User access URL>?Relay State=https://fed.adp.com/saml/fedlanding.html?REDBOX`

9. **Enregistrez** vos modifications.

10. Une fois la confirmation reçue de votre représentant ADP, commencez à effectuer un test avec un ou deux utilisateurs.

    a. Assignez quelques utilisateurs à l’application de service ADP pour tester l’accès fédéré.

    b. Le test est réussi quand les utilisateurs accèdent à l’application de service ADP dans la galerie et qu’ils peuvent accéder à leur service ADP.
 
11. Une fois confirmée la réussite d’un test, assignez le service ADP fédéré à des utilisateurs ou à des groupes d’utilisateurs, comme expliqué plus loin dans le didacticiel, et déployez-le pour vos employés. 

> [!TIP]
> Vous pouvez maintenant lire une version concise de ces instructions dans le [portail Azure](https://portal.azure.com), pendant que vous configurez l’application.  Après avoir ajouté cette application à partir de la section **Active Directory > Applications d’entreprise**, cliquez simplement sur l’onglet **Authentification unique** et accédez à la documentation incorporée par le biais de la section **Configuration** en bas. Vous pouvez en savoir plus sur la fonctionnalité de documentation incorporée ici : [Documentation incorporée Azure AD]( https://go.microsoft.com/fwlink/?linkid=845985)
> 

### <a name="create-an-azure-ad-test-user"></a>Créer un utilisateur de test Azure AD

L’objectif de cette section est de créer un utilisateur de test appelé Britta Simon dans le portail Azure.

   ![Créer un utilisateur de test Azure AD][100]

**Pour créer un utilisateur de test dans Azure AD, procédez comme suit :**

1. Dans le volet gauche du Portail Azure, cliquez sur le bouton **Azure Active Directory**.

    ![Bouton Azure Active Directory](./media/active-directory-saas-adpfederatedsso-tutorial/create_aaduser_01.png)

2. Pour afficher la liste des utilisateurs, accédez à **Utilisateurs et groupes**, puis cliquez sur **Tous les utilisateurs**.

    ![Liens « Utilisateurs et groupes » et « Tous les utilisateurs »](./media/active-directory-saas-adpfederatedsso-tutorial/create_aaduser_02.png)

3. Pour ouvrir la boîte de dialogue **Utilisateur**, cliquez sur **Ajouter** en haut de la boîte de dialogue **Tous les utilisateurs**.

    ![Bouton Ajouter](./media/active-directory-saas-adpfederatedsso-tutorial/create_aaduser_03.png)

4. Dans la boîte de dialogue **Utilisateur**, procédez comme suit :

    ![Boîte de dialogue Utilisateur](./media/active-directory-saas-adpfederatedsso-tutorial/create_aaduser_04.png)

    a. Dans la zone **Nom**, tapez **BrittaSimon**.

    b. Dans la zone **Nom d’utilisateur** , tapez l’adresse e-mail de l’utilisateur Britta Simon.

    c. Cochez la case **Afficher le mot de passe**, puis notez la valeur affichée dans le champ **Mot de passe**.

    d. Cliquez sur **Créer**.
 
### <a name="create-an-adp-federated-sso-test-user"></a>Créer un utilisateur de test ADP Federated SSO

L’objectif de cette section est de créer un utilisateur appelé Britta Simon dans ADP Federated SSO. Pour ajouter les utilisateurs au compte ADP Federated SSO, contactez [l’équipe du support ADP](https://www.adp.com/contact-us/overview.aspx).

### <a name="assign-the-azure-ad-test-user"></a>Affecter l’utilisateur de test Azure AD

Dans cette section, vous allez autoriser Britta Simon à utiliser l’authentification unique Azure en lui accordant l’accès à ADP Federated SSO.

![Attribuer le rôle utilisateur][200] 

**Pour affecter Britta Simon à ADP Federated SSO, effectuez les étapes suivantes :**

1. Dans le portail Azure, ouvrez la vue des applications, accédez à la vue des répertoires, accédez à **Applications d’entreprise**, puis cliquez sur **Toutes les applications**.

    ![Affecter des utilisateurs][201] 

2. Dans la liste des applications, sélectionnez **ADP Federated SSO**.

    ![Lien ADP Federated SSO dans la liste des applications](./media/active-directory-saas-adpfederatedsso-tutorial/tutorial_adpfederatedsso_app.png)  

3. Dans le menu de gauche, cliquez sur **Utilisateurs et groupes**.

    ![Lien « Utilisateurs et groupes »][202]

4. Cliquez sur le bouton **Ajouter**. Ensuite, sélectionnez **Utilisateurs et groupes** dans la boîte de dialogue **Ajouter une affectation**.

    ![Volet Ajouter une attribution][203]

5. Dans la boîte de dialogue **Utilisateurs et groupes**, sélectionnez **Britta Simon** dans la liste des utilisateurs.

6. Cliquez sur le bouton **Sélectionner** dans la boîte de dialogue **Utilisateurs et groupes**.

7. Cliquez sur le bouton **Affecter** dans la boîte de dialogue **Ajouter une affectation**.
    
### <a name="test-single-sign-on"></a>Tester l’authentification unique

Dans cette section, vous allez tester la configuration de l’authentification unique Azure AD à l’aide du volet d’accès.

Quand vous cliquez sur la vignette ADP Federated SSO dans le volet d’accès, vous devez être connecté automatiquement à votre application ADP Federated SSO.
Pour plus d’informations sur le panneau d’accès, consultez [Présentation du panneau d’accès](active-directory-saas-access-panel-introduction.md). 

## <a name="additional-resources"></a>Ressources supplémentaires

* [Liste de didacticiels sur l’intégration d’applications SaaS avec Azure Active Directory](active-directory-saas-tutorial-list.md)
* [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](active-directory-appssoaccess-whatis.md)



<!--Image references-->

[1]: ./media/active-directory-saas-adpfederatedsso-tutorial/tutorial_general_01.png
[2]: ./media/active-directory-saas-adpfederatedsso-tutorial/tutorial_general_02.png
[3]: ./media/active-directory-saas-adpfederatedsso-tutorial/tutorial_general_03.png
[4]: ./media/active-directory-saas-adpfederatedsso-tutorial/tutorial_general_04.png

[100]: ./media/active-directory-saas-adpfederatedsso-tutorial/tutorial_general_100.png

[200]: ./media/active-directory-saas-adpfederatedsso-tutorial/tutorial_general_200.png
[201]: ./media/active-directory-saas-adpfederatedsso-tutorial/tutorial_general_201.png
[202]: ./media/active-directory-saas-adpfederatedsso-tutorial/tutorial_general_202.png
[203]: ./media/active-directory-saas-adpfederatedsso-tutorial/tutorial_general_203.png


---

copyright:
  years: 2015, 2016
lastupdated: "2016-11-07"

---
{:new_window: target="_blank"}
{:codeblock:.codeblock}

# Initialisation de BMSClient
{: #sdk_BMSClient}

`BMSCore` fournit l'infrastructure HTTP que les autres logiciels SDK client des services {{site.data.keyword.Bluemix}} Mobile utilisent pour communiquer avec leurs services {{site.data.keyword.Bluemix_notm}} correspondants.


## Initialisation de votre application Android
{: #init-BMSClient-android}

Vous pouvez télécharger et importer le module `BMSCore` dans votre projet Android Studio ou utiliser Gradle.

1. Importez le logiciel SDK du client en ajoutant l'instruction `import` suivante au début de votre fichier de projet :

  ```
  import com.ibm.mobilefirstplatform.clientsdk.android.core.api.*;
  ```
  {: codeblock}

2. Initialisez le logiciel SDK `BMSCore` dans votre application Android en ajoutant le code d'initialisation dans la méthode `onCreate` de l'activité principale de votre application Android ou à l'emplacement le plus approprié pour votre projet.

	```Java
	BMSClient.getInstance().initialize(getApplicationContext(), BMSClient.REGION_US_SOUTH); // Make sure that you point to your region
	```
	{: codeblock}

  Vous devez initialiser la classe `BMSClient` à l'aide du paramètre **bluemixRegion**. Dans
l'initialiseur, la valeur **bluemixRegion** spécifie le déploiement {{site.data.keyword.Bluemix_notm}} que vous utilisez, par
exemple `BMSClient.REGION_US_SOUTH`, `BMSClient.REGION_UK` ou `BMSClient.REGION_SYDNEY`.


## Initialisation de votre application iOS
{: #init-BMSClient-ios}

Vous pouvez utiliser [CocoaPods](https://cocoapods.org){: new_window} ou [Carthage](https://github.com/Carthage/Carthage){: new_window} pour obtenir le module `BMSCore`.

1. Pour installer `BMSCore` en utilisant CocoaPods, ajoutez les lignes suivantes à votre Podfile. Si votre projet n'a pas encore de Podfile, utilisez la commande `pod init`.

  ```Swift
  use_frameworks!

  target 'MyApp' do
    pod 'BMSCore'
  end
  ```
  {: codeblock}

  Ensuite, exécutez la commande `pod install` et ouvrez le fichier `.xcworkspace` généré. Pour mettre à jour vers une version plus récente de `BMSCore`, utilisez `pod update BMSCore`.

  Pour plus d'informations sur l'utilisation de CocoaPods, voir les [CocoaPods Guides](https://guides.cocoapods.org/using/index.html){: new_window}.

2. Pour installer `BMSCore` en utilisant Carthage, suivez ces [instructions](https://github.com/Carthage/Carthage#getting-started){: new_window}.

  1. Ajoutez la ligne suivante à votre Cartfile :

      ```
      github "ibm-bluemix-mobile-services/bms-clientsdk-swift-core"
      ```
      {: codeblock}

  2. Exécutez la commande `carthage update`. 

  3. Une fois la génération terminée, ajoutez `BMSCore.framework` à votre projet en effectuant l'[étape 3](https://github.com/Carthage/Carthage#getting-started) dans les instructions Carthage.

  Pour les applications construites avec Swift 2.3, utilisez la commande `carthage update --toolchain com.apple.dt.toolchain.Swift_2_3`. Sinon, utilisez la commande `carthage update`.

3. Importez le module.

  ```Swift
  import BMSCore
  ```
  {: codeblock}

4. Initialisez la classe `BMSClient` à l'aide du code suivant :

  Placez le code d'initialisation dans la méthode `application(_:didFinishLaunchingWithOptions:)` de votre délégué d'application ou à l'emplacement le plus approprié pour votre projet.

    ```Swift
    BMSClient.sharedInstance.initialize(bluemixRegion: BMSClient.Region.usSouth) // Prenez soin de pointer sur votre région
    ```
   {: codeblock}

    Pour utiliser le logiciel SDK du client {{site.data.keyword.mobileanalytics_short}}, vous devez d'abord initialiser la classe `BMSClient` à l'aide du paramètre **bluemixRegion**. Dans
l'initialiseur, la valeur **bluemixRegion** spécifie le déploiement {{site.data.keyword.Bluemix_notm}} que vous utilisez, par
exemple `BMSClient.Region.usSouth`, `BMSClient.Region.unitedKingdom` ou `BMSClient.Region.sydney`.

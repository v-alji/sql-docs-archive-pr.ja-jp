---
title: Reporting Services サービスアプリケーションの電子メールの構成 (SharePoint 2010 および SharePoint 2013) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 38fc34a6-aae7-4dde-9ad2-f1eee0c42a9f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 628122289f8a9d83a307d70a369ab51f8f571c04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642594"
---
# <a name="configure-e-mail-for-a-reporting-services-service-application-sharepoint-2010-and-sharepoint-2013"></a><span data-ttu-id="81ecd-102">Reporting Services サービス アプリケーションの電子メールの構成 (SharePoint 2010 および SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="81ecd-102">Configure E-mail for a Reporting Services Service Application (SharePoint 2010 and SharePoint 2013)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="81ecd-103">のデータ警告機能は、電子メール メッセージで警告を送信します。</span><span class="sxs-lookup"><span data-stu-id="81ecd-103">data alerting sends alerts in e-mail messages.</span></span> <span data-ttu-id="81ecd-104">電子メールを送信するには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションを構成して、このサービス アプリケーションの電子メール配信拡張機能を変更しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="81ecd-104">To send e-mail you may need to configure your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application and you may need to modify the e-mail delivery extension for the service application.</span></span> <span data-ttu-id="81ecd-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サブスクリプション機能の電子メール配信拡張機能を使用する場合、電子メールの設定も必要です。</span><span class="sxs-lookup"><span data-stu-id="81ecd-105">The e-mail settings are also required if you plan to use the e-mail delivery extension for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscription feature.</span></span>  
  
||  
|-|  
|[!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="81ecd-106">Sharepoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] モード &#124; sharepoint 2010 および sharepoint 2013。</span><span class="sxs-lookup"><span data-stu-id="81ecd-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode &#124; SharePoint 2010 and SharePoint 2013.</span></span>|  
  
### <a name="to-configure-e-mail-for-the-shared-service"></a><span data-ttu-id="81ecd-107">共有サービスの電子メールを構成するには</span><span class="sxs-lookup"><span data-stu-id="81ecd-107">To configure e-mail for the shared service</span></span>  
  
1.  <span data-ttu-id="81ecd-108">SharePoint の全体管理で **[アプリケーション管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="81ecd-108">In SharePoint Central Administration, click the **Application Management**.</span></span>  
  
2.  <span data-ttu-id="81ecd-109">**[サービス アプリケーション]** グループで、 **[サービス アプリケーションの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="81ecd-109">In the **Service Applications** group, click **Manage service applications**.</span></span>  
  
3.  <span data-ttu-id="81ecd-110">**[名前]** ボックスの一覧で、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="81ecd-110">In the **Name** list, click the name of your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
4.  <span data-ttu-id="81ecd-111">**[Reporting Services アプリケーションの管理]** ページの **[電子メールの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="81ecd-111">Click **E-mail Settings** on the **Manage Reporting Services Application** page.</span></span>  
  
5.  <span data-ttu-id="81ecd-112">**[SMTP サーバーの使用]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="81ecd-112">Select **Use SMTP server**.</span></span>  
  
6.  <span data-ttu-id="81ecd-113">**[送信 SMTP サーバー]** ボックスに、SMTP サーバーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="81ecd-113">In the **Outbound SMTP server** box, type the name of an SMTP server.</span></span>  
  
7.  <span data-ttu-id="81ecd-114">**[差出人アドレス]** ボックスに、電子メール アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="81ecd-114">In the **From address** box, type an e-mail address.</span></span>  
  
     <span data-ttu-id="81ecd-115">このアドレスはすべての警告電子メール メッセージの送信元になります。</span><span class="sxs-lookup"><span data-stu-id="81ecd-115">This address is the sender of all alert e-mail messages.</span></span>  
  
     <span data-ttu-id="81ecd-116">**[差出人アドレス]** に指定するユーザーのアカウントは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションのアプリケーション プールを構成するときに指定した管理アカウントである必要があります。</span><span class="sxs-lookup"><span data-stu-id="81ecd-116">The account of the user specified in **From address** must be a managed account that you specified when you configured the application pool for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="81ecd-117">権限がある場合、SharePoint サーバーの全体管理の [サービス アカウント] ページで既存の管理アカウントの一覧を表示できます。</span><span class="sxs-lookup"><span data-stu-id="81ecd-117">If you have permission, you can view a list of existing managed accounts on the Service Accounts page in SharePoint Central Administration.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="ntlm-authentication"></a><span data-ttu-id="81ecd-118">NTLM 認証</span><span class="sxs-lookup"><span data-stu-id="81ecd-118">NTLM Authentication</span></span>  
  
1.  <span data-ttu-id="81ecd-119">NTLM 認証を必要とする電子メール環境で匿名アクセスを許可しない場合、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションの電子メール配信拡張機能の構成を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81ecd-119">If your email environment requires NTLM authentication and does not allow anonymous access, you need to modify the e-mail delivery extension configuration for your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications.</span></span> <span data-ttu-id="81ecd-120">**Smtpauthenticate**を、値 "2" を使用するように変更します。</span><span class="sxs-lookup"><span data-stu-id="81ecd-120">Change the **SMTPAuthenticate** to use a value of "2".</span></span> <span data-ttu-id="81ecd-121">この値はユーザー インターフェイスから変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="81ecd-121">This value cannot be changed from the user interface.</span></span> <span data-ttu-id="81ecd-122">次の PowerShell スクリプトの例では、"SSRS_TESTAPPLICATION" という名前のサービス アプリケーションについて、レポート サーバーの電子メール配信拡張機能の構成全体を更新します。</span><span class="sxs-lookup"><span data-stu-id="81ecd-122">The following PowerShell script example, updates the full configuration for the report server e-mail delivery extension for the service application named "SSRS_TESTAPPLICATION".</span></span> <span data-ttu-id="81ecd-123">スクリプトに示されているノードの一部は、[差出人アドレス] などのユーザー インターフェイスからも設定できます。</span><span class="sxs-lookup"><span data-stu-id="81ecd-123">Note some of the nodes listed in the script can also be set from the user interface, for example the "From" address.</span></span>  
  
    ```powershell
    $app = Get-SPRSServiceApplication | Where {$_.name -like "SSRS_TESTAPPLICATION *"}  
    $emailCfg = Get-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml
    $emailXml = [xml]$emailCfg
    $emailXml.SelectSingleNode("//SMTPServer").InnerText = "your email server name"  
    $emailXml.SelectSingleNode("//SendUsing").InnerText = "2"  
    $emailXml.SelectSingleNode("//SMTPAuthenticate").InnerText = "2"  
    $emailXml.SelectSingleNode("//From").InnerText = "your FROM email address"  
    Set-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" -ExtensionConfiguration $emailXml.OuterXml  
    ```  
  
2.  <span data-ttu-id="81ecd-124">サービスアプリケーションの名前を確認する必要がある場合は、 **get-sprsserviceapplication**コマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="81ecd-124">If you need to verify the name of your service application, run the **Get-SPRSServiceApplication** cmdlet.</span></span>  
  
    ```powershell
    Get-SPRSServiceApplication  
    ```  
  
3.  <span data-ttu-id="81ecd-125">次の例では、"SSRS_TESTAPPLICATION" という名前のサービス アプリケーションについて、電子メール拡張機能の現在の値を返します。</span><span class="sxs-lookup"><span data-stu-id="81ecd-125">The following example will return the current values of the e-mail extension for the service application named "SSRS_TESTAPPLICATION".</span></span>  
  
    ```powershell
    $app = get-sprsserviceapplication | Where {$_.name -like "SSRSTEST_APPLICATION*"}  
    Get-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml  
    ```  
  
4.  <span data-ttu-id="81ecd-126">次の例では、"SSRS_TESTAPPLICATION" という名前のサービス アプリケーションについて、電子メール拡張機能の現在の値を使用して "emailconfig.txt" という名前の新規ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="81ecd-126">The following example will create a new file named "emailconfig.txt" with the current values of the e-mail extension for the service application named "SSRS_TESTAPPLICATION"</span></span>  
  
    ```powershell
    $app = Get-SPRSServiceApplication | Where {$_.name -like "SSRS_TESTAPPLICATION*"}  
    Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | Select -ExpandProperty ConfigurationXml | Out-File c:\emailconfig.txt  
    ```

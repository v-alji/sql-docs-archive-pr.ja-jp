---
title: レポート サーバーでカスタム認証またはフォーム認証を構成する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Forms authentication, configuring
- custom authentication [Reporting Services]
ms.assetid: e8601a8f-e66d-4649-8e4d-a46ca20ec7d0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1447e1e695f0e59dbc07b7e19f4df335a1220a97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633723"
---
# <a name="configure-custom-or-forms-authentication-on-the-report-server"></a><span data-ttu-id="f13ca-102">レポート サーバーでカスタム認証またはフォーム認証を構成する</span><span class="sxs-lookup"><span data-stu-id="f13ca-102">Configure Custom or Forms Authentication on the Report Server</span></span>
  <span data-ttu-id="f13ca-103">Reporting Services に用意されている拡張可能なアーキテクチャを使用すると、カスタム認証モジュールまたはフォームベースの認証モジュールを組み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="f13ca-103">Reporting Services provides an extensible architecture that allows you to plug in custom or forms-based authentication modules.</span></span> <span data-ttu-id="f13ca-104">配置の要件に Windows 統合セキュリティまたは基本認証が含まれていない場合は、カスタム認証拡張機能を実装することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="f13ca-104">You might consider implementing a custom authentication extension if deployment requirements do not include Windows integrated security or Basic authentication.</span></span> <span data-ttu-id="f13ca-105">カスタム認証を使用する最も一般的なシナリオは、インターネットまたはエクストラネットを介した Web アプリケーションへのアクセスをサポートすることです。</span><span class="sxs-lookup"><span data-stu-id="f13ca-105">The most common scenario for using custom authentication is to support Internet or extranet access to a Web application.</span></span> <span data-ttu-id="f13ca-106">既定の Windows 認証拡張機能の代わりにカスタム認証拡張機能を使用することで、レポート サーバーへのアクセスを外部ユーザーに許可する方法をより細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="f13ca-106">Replacing the default Windows Authentication extension with a custom authentication extension gives you more control over how external users are granted access to the report server.</span></span>  
  
 <span data-ttu-id="f13ca-107">実際に、カスタム認証拡張機能を配置するには、アセンブリとアプリケーション ファイルのコピー、構成ファイルの変更、テストを含む、複数の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f13ca-107">In practice, deploying a custom authentication extension requires multiple steps that include copying assemblies and application files, modifying configuration files, and testing.</span></span> <span data-ttu-id="f13ca-108">ここでは、構成ファイルで指定する認証設定のみに焦点を当てて説明します。</span><span class="sxs-lookup"><span data-stu-id="f13ca-108">This topic focuses on just the authentication settings that you specify in the configuration files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f13ca-109">カスタム認証拡張機能を作成するには、カスタム コードと [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] セキュリティに関する専門知識が必要です。</span><span class="sxs-lookup"><span data-stu-id="f13ca-109">Creating a custom authentication extension requires custom code and expertise in [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] security.</span></span> <span data-ttu-id="f13ca-110">カスタム認証拡張機能を作成しない場合は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory のグループとアカウントを使用できます。ただし、レポート サーバーの配置のスコープを大幅に縮小する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f13ca-110">If you do not want to create a custom authentication extension, you can use [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory groups and accounts, but you should greatly reduce the scope of a report server deployment.</span></span> <span data-ttu-id="f13ca-111">カスタム認証について詳しくは、「 [セキュリティ拡張機能の実装](../extensions/security-extension/implementing-a-security-extension.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f13ca-111">For more information about custom authentication, see [Implementing a Security Extension](../extensions/security-extension/implementing-a-security-extension.md).</span></span>  
  
 <span data-ttu-id="f13ca-112">さらに、SharePoint 製品と統合された [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 環境でフォーム認証またはカスタム認証拡張機能を使用する場合は、選択した認証方法を使用するように SharePoint サイトを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f13ca-112">Additionally, if you want to use Forms authentication or a custom authentication extension in a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] environment that is integrated with a SharePoint product, you must configure the SharePoint site to use the authentication method that you choose.</span></span> <span data-ttu-id="f13ca-113">SharePoint における認証の構成に関する詳細については、 [Developer Network (MSDN) の「](https://go.microsoft.com/fwlink/?LinkId=115575) 認証の例 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f13ca-113">For more information about configuring authentication in SharePoint, see [Authentication Samples](https://go.microsoft.com/fwlink/?LinkId=115575) on [!INCLUDE[msCoName](../../includes/msconame-md.md)] Developer Network (MSDN).</span></span>  
  
### <a name="to-configure-a-report-server-to-use-custom-authentication"></a><span data-ttu-id="f13ca-114">カスタム認証を使用するようにレポート サーバーを構成するには</span><span class="sxs-lookup"><span data-stu-id="f13ca-114">To configure a report server to use Custom authentication</span></span>  
  
1.  <span data-ttu-id="f13ca-115">テキスト エディターで RSReportServer.config を開きます。</span><span class="sxs-lookup"><span data-stu-id="f13ca-115">Open RSReportServer.config in a text editor.</span></span>  
  
2.  <span data-ttu-id="f13ca-116"><`Authentication`> を検索します。</span><span class="sxs-lookup"><span data-stu-id="f13ca-116">Find <`Authentication`>.</span></span>  
  
3.  <span data-ttu-id="f13ca-117">次の XML 構造をコピーします。</span><span class="sxs-lookup"><span data-stu-id="f13ca-117">Copy the following XML structure:</span></span>  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <Custom />  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    </Authentication>  
    ```  
  
4.  <span data-ttu-id="f13ca-118"><> の既存のエントリの上に貼り付け `Authentication` ます。</span><span class="sxs-lookup"><span data-stu-id="f13ca-118">Paste it over the existing entries for <`Authentication`>.</span></span>  
  
     <span data-ttu-id="f13ca-119">`Custom` は他の認証の種類と併用できないので注意してください。</span><span class="sxs-lookup"><span data-stu-id="f13ca-119">Note that you cannot use `Custom` with other authentication types.</span></span>  
  
5.  <span data-ttu-id="f13ca-120">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="f13ca-120">Save the file.</span></span>  
  
6.  <span data-ttu-id="f13ca-121">レポート サーバーの Web.config ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="f13ca-121">Open the Web.config file for the report server.</span></span> <span data-ttu-id="f13ca-122">既定では、このファイルは \Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\ReportServer にあります。</span><span class="sxs-lookup"><span data-stu-id="f13ca-122">By default, it is located at \Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\ReportServer.</span></span>  
  
7.  <span data-ttu-id="f13ca-123">検索 `authentication mode` して設定 `Forms` します。</span><span class="sxs-lookup"><span data-stu-id="f13ca-123">Find `authentication mode` and set it `Forms`.</span></span>  
  
    ```  
    <authentication mode = "Forms" />  
    ```  
  
8.  <span data-ttu-id="f13ca-124">`identity impersonate` を探して、`False` を設定します。</span><span class="sxs-lookup"><span data-stu-id="f13ca-124">Find `identity impersonate` and set it to `False`.</span></span>  
  
    ```  
    <identity impersonate = "false" />  
    ```  
  
9. <span data-ttu-id="f13ca-125">レポート マネージャーの Web.config ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="f13ca-125">Open the Web.config file for Report Manager.</span></span> <span data-ttu-id="f13ca-126">既定では、このファイルは \Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\ReportManager にあります。</span><span class="sxs-lookup"><span data-stu-id="f13ca-126">By default, it is located at \Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\ReportManager.</span></span>  
  
10. <span data-ttu-id="f13ca-127">検索 `authentication mode` して設定 `Forms` します。</span><span class="sxs-lookup"><span data-stu-id="f13ca-127">Find `authentication mode` and set it `Forms`.</span></span>  
  
    ```  
    <authentication mode = "Forms" />  
    ```  
  
11. <span data-ttu-id="f13ca-128">`identity impersonate` を探して、`False` を設定します。</span><span class="sxs-lookup"><span data-stu-id="f13ca-128">Find `identity impersonate` and set it to `False`.</span></span>  
  
    ```  
    <identity impersonate = "false" />  
    ```  
  
12. <span data-ttu-id="f13ca-129">構成ファイルに `PassThroughCookies` 要素構造を追加します。</span><span class="sxs-lookup"><span data-stu-id="f13ca-129">Add the `PassThroughCookies` element structure to the configuration file.</span></span> <span data-ttu-id="f13ca-130">詳しくは、「 [カスタム認証クッキーを送信するようにレポート マネージャーを構成する](configure-the-web-portal-to-pass-custom-authentication-cookies.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f13ca-130">For more information, see [Configure Report Manager to Pass Custom Authentication Cookies](configure-the-web-portal-to-pass-custom-authentication-cookies.md).</span></span>  
  
13. <span data-ttu-id="f13ca-131">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="f13ca-131">Save the file.</span></span>  
  
14. <span data-ttu-id="f13ca-132">スケールアウト配置を構成した場合は、配置内の他のレポート サーバーに対して上記の手順すべてを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="f13ca-132">If you configured a scale-out deployment, repeat all of the previous steps for other report servers in the deployment.</span></span>  
  
15. <span data-ttu-id="f13ca-133">レポート サーバーを再起動して、現在開いているセッションを消去します。</span><span class="sxs-lookup"><span data-stu-id="f13ca-133">Restart the report server to clear any sessions that are currently open.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f13ca-134">参照</span><span class="sxs-lookup"><span data-stu-id="f13ca-134">See Also</span></span>  
 <span data-ttu-id="f13ca-135">[セキュリティ拡張機能の実装](../extensions/security-extension/implementing-a-security-extension.md) </span><span class="sxs-lookup"><span data-stu-id="f13ca-135">[Implementing a Security Extension](../extensions/security-extension/implementing-a-security-extension.md) </span></span>  
 <span data-ttu-id="f13ca-136">[レポート サーバーでの認証](authentication-with-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="f13ca-136">[Authentication with the Report Server](authentication-with-the-report-server.md) </span></span>  
 <span data-ttu-id="f13ca-137">[RSReportServer 構成ファイル](../report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="f13ca-137">[RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="f13ca-138">[レポートサーバーで基本認証を構成する](configure-basic-authentication-on-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="f13ca-138">[Configure Basic Authentication on the Report Server](configure-basic-authentication-on-the-report-server.md) </span></span>  
 [<span data-ttu-id="f13ca-139">レポート サーバーで Windows 認証を構成する</span><span class="sxs-lookup"><span data-stu-id="f13ca-139">Configure Windows Authentication on the Report Server</span></span>](configure-windows-authentication-on-the-report-server.md)  
  
  

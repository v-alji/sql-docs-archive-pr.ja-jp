---
title: 登録済みのフィルターおよびワード ブレーカーの表示または変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], word breakers
- full-text search [SQL Server], filters
- filters [full-text search]
- word breakers [full-text search]
ms.assetid: f88c54df-b1aa-4701-807f-dc92c32363fd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 79ad7f1f7df15fed21a132bbe253adc7185d8c06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714094"
---
# <a name="view-or-change-registered-filters-and-word-breakers"></a><span data-ttu-id="d4ab3-102">登録済みのフィルターおよびワード ブレーカーの表示または変更</span><span class="sxs-lookup"><span data-stu-id="d4ab3-102">View or Change Registered Filters and Word Breakers</span></span>
  <span data-ttu-id="d4ab3-103">システム上で任意のワード ブレーカーまたはフィルターのインストールまたはアンインストールを行った後、その変更はサーバー インスタンスに自動的に反映されません。</span><span class="sxs-lookup"><span data-stu-id="d4ab3-103">After any word breakers or filters are installed or uninstalled on a system, the changes do not automatically take effect on server instances.</span></span> <span data-ttu-id="d4ab3-104">このトピックでは、現在登録されているワード ブレーカーまたはフィルターを表示する方法と、新しくインストールされたワード ブレーカーおよびフィルターを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに登録する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d4ab3-104">This topic describes how to view the currently registered word breaker or filters and how to register newly installed word breakers and filters on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="to-view-a-list-of-languages-whose-word-breakers-are-currently-registered"></a><span data-ttu-id="d4ab3-105">ワード ブレーカーが現在登録されている言語の一覧を表示するには</span><span class="sxs-lookup"><span data-stu-id="d4ab3-105">To view a list of languages whose word breakers are currently registered</span></span>  
  
1.  <span data-ttu-id="d4ab3-106">[sys.fulltext_languages](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql) カタログ ビューを使用します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d4ab3-106">Use the [sys.fulltext_languages](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql) catalog view, as follows:</span></span>  
  
    ```  
    SELECT * FROM sys.fulltext_languages;   
    ```  
  
### <a name="to-view-a-list-of-the-filters-that-are-currently-registered"></a><span data-ttu-id="d4ab3-107">現在登録されているフィルターの一覧を表示するには</span><span class="sxs-lookup"><span data-stu-id="d4ab3-107">To view a list of the filters that are currently registered</span></span>  
  
1.  <span data-ttu-id="d4ab3-108">[sp_help_fulltext_system_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) システム ストアド プロシージャを使用します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d4ab3-108">Use the [sp_help_fulltext_system_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) system stored procedure, as follows:</span></span>  
  
    ```  
    EXEC sp_help_fulltext_system_components 'filter';    
    ```  
  
### <a name="to-register-newly-installed-word-breakers-and-filters"></a><span data-ttu-id="d4ab3-109">新しくインストールされたワード ブレーカーおよびフィルターを登録するには</span><span class="sxs-lookup"><span data-stu-id="d4ab3-109">To register newly installed word breakers and filters</span></span>  
  
1.  <span data-ttu-id="d4ab3-110">[sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql) システム ストアド プロシージャを使用して、言語の一覧を更新します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d4ab3-110">Use the [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql) system stored procedure to update the list of languages, as follows:</span></span>  
  
    ```  
    exec sp_fulltext_service 'update_languages';   
    ```  
  
### <a name="to-unregister-uninstalled-word-breakers-and-filters"></a><span data-ttu-id="d4ab3-111">アンインストールされたワード ブレーカーおよびフィルターを登録解除するには</span><span class="sxs-lookup"><span data-stu-id="d4ab3-111">To unregister uninstalled word breakers and filters</span></span>  
  
1.  <span data-ttu-id="d4ab3-112">**sp_fulltext_service** を使用して、言語の一覧を更新します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d4ab3-112">Use the **sp_fulltext_service** to update the list of languages, as follows:</span></span>  
  
    ```  
    exec sp_fulltext_service 'update_languages'  
    ```  
  
2.  <span data-ttu-id="d4ab3-113">**sp_fulltext_service** を使用して、フィルター デーモン ホスト プロセス (fdhost.exe) を起動します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d4ab3-113">Use the **sp_fulltext_service** to restart the filter daemon host processes (fdhost.exe), as follows:</span></span>  
  
    ```  
    exec sp_fulltext_service 'restart_all_fdhosts';  
    ```  
  
### <a name="to-replace-existing-word-breakers-or-filters-when-installing-new-ones"></a><span data-ttu-id="d4ab3-114">新しいワード ブレーカーまたはフィルターのインストール時に既存のワード ブレーカーまたはフィルターを置き換えるには</span><span class="sxs-lookup"><span data-stu-id="d4ab3-114">To replace existing word breakers or filters when installing new ones</span></span>  
  
1.  <span data-ttu-id="d4ab3-115">新しいワード ブレーカーまたはフィルターを含む DLL ファイルのインストールを準備するときに、そのファイル名サーバー インスタンスにインストールされている既存の DLL ファイルとは異なることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d4ab3-115">When preparing to install a DLL file that contains new word breakers or filters, verify that it has a different filename from any of the existing DLL files installed on your server instance.</span></span>  
  
2.  <span data-ttu-id="d4ab3-116">サーバー インスタンスの標準 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DLL ファイルが格納されているディレクトリに新しい DLL ファイルをコピーします。</span><span class="sxs-lookup"><span data-stu-id="d4ab3-116">Copy the new DLL file into the directory containing the standard [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DLL files for the server instance.</span></span> <span data-ttu-id="d4ab3-117">既定の場所は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d4ab3-117">The default location is:</span></span>  
  
     <span data-ttu-id="d4ab3-118">C:\Program Files\Microsoft SQL Server\MSSQL.*instance_name*\MSSQL\Binn</span><span class="sxs-lookup"><span data-stu-id="d4ab3-118">C:\Program Files\Microsoft SQL Server\MSSQL.*instance_name*\MSSQL\Binn</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d4ab3-119">署名付きの検証されたコンポーネントのみを読み込むようにすることを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d4ab3-119">We highly recommend that you load only signed and verified components.</span></span> <span data-ttu-id="d4ab3-120">さらに、FDHOST ランチャー (MSSQLFDLauncher) サービスは、必要最小限の特権で実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d4ab3-120">Also, we recommend that you run the FDHOST Launcher (MSSQLFDLauncher) Service with the least possible privileges.</span></span>  
  
3.  <span data-ttu-id="d4ab3-121">新しいワード ブレーカーまたはフィルターをインストールします。</span><span class="sxs-lookup"><span data-stu-id="d4ab3-121">Install the new word breaker or filters.</span></span>  
  
     <span data-ttu-id="d4ab3-122">**Microsoft Filter Pack IFilters をインストールして読み込むには**</span><span class="sxs-lookup"><span data-stu-id="d4ab3-122">**To install and load Microsoft Filter Pack IFilters**</span></span>  
  
    -   [<span data-ttu-id="d4ab3-123">How to register Microsoft Filter Pack IFilters with SQL Server (Microsoft Filter Pack の IFilter を SQL Server に登録する方法)</span><span class="sxs-lookup"><span data-stu-id="d4ab3-123">How to register Microsoft Filter Pack IFilters with SQL Server</span></span>](https://go.microsoft.com/fwlink/?LinkId=130439)  
  
4.  <span data-ttu-id="d4ab3-124">**sp_fulltext_service** を使用して、新しくインストールされたワード ブレーカーおよびフィルターをサーバー インスタンスに読み込みます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d4ab3-124">Use **sp_fulltext_service** to load newly installed word breakers and filters in the server instance, as follows:</span></span>  
  
    ```  
    EXEC sp_fulltext_service @action='load_os_resources', @value=1;  
    ```  
  
5.  <span data-ttu-id="d4ab3-125">**sp_fulltext_service** を使用して、言語の一覧を更新します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d4ab3-125">Use **sp_fulltext_service** to update the list of languages, as follows:</span></span>  
  
    ```  
    EXEC sp_fulltext_service 'update_languages';  
    ```  
  
6.  <span data-ttu-id="d4ab3-126">**sp_fulltext_service** を使用して、フィルター デーモン ホスト プロセス (fdhost.exe) を再起動します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d4ab3-126">Restart the filter daemon host processes (fdhost.exe), using **sp_fulltext_service** as follows:</span></span>  
  
    ```  
    EXEC sp_fulltext_service 'restart_all_fdhosts';   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d4ab3-127">参照</span><span class="sxs-lookup"><span data-stu-id="d4ab3-127">See Also</span></span>  
 <span data-ttu-id="d4ab3-128">[フルテキスト フィルター デーモン ランチャーのサービス アカウントの設定](set-the-service-account-for-the-full-text-filter-daemon-launcher.md) </span><span class="sxs-lookup"><span data-stu-id="d4ab3-128">[Set the Service Account for the Full-text Filter Daemon Launcher](set-the-service-account-for-the-full-text-filter-daemon-launcher.md) </span></span>  
 <span data-ttu-id="d4ab3-129">[検索用フィルターの構成と管理](configure-and-manage-filters-for-search.md) </span><span class="sxs-lookup"><span data-stu-id="d4ab3-129">[Configure and Manage Filters for Search](configure-and-manage-filters-for-search.md) </span></span>  
 [<span data-ttu-id="d4ab3-130">検索用のワード ブレーカーとステミング機能の構成と管理</span><span class="sxs-lookup"><span data-stu-id="d4ab3-130">Configure and Manage Word Breakers and Stemmers for Search</span></span>](configure-and-manage-word-breakers-and-stemmers-for-search.md)  
  
  

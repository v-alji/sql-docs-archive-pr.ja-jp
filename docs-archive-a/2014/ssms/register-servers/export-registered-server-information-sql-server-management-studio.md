---
title: 登録済みサーバーの情報のエクスポート
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.exportregisteredservers.f1
helpviewer_keywords:
- Registered Servers [SQL Server], exporting
- exporting registered server information
- transferring registered server information
ms.assetid: b65e168f-b6bf-489c-b8ad-3b8644acf0b6
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 03092de2d722e8f8b807dbb3d23c4b4e2b91f6f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737399"
---
# <a name="export-registered-server-information-sql-server-management-studio"></a><span data-ttu-id="5a489-102">登録済みサーバー情報のエクスポート (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="5a489-102">Export Registered Server Information (SQL Server Management Studio)</span></span>
  <span data-ttu-id="5a489-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]で登録済みサーバーの情報を保存およびエクスポートして、他の従業員またはサーバーに配布する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5a489-103">This topic describes how to save and export registered server information in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]and distribute it to other employees or servers.</span></span> <span data-ttu-id="5a489-104">このエクスポート機能を使用すると、複数のコンピューターに一貫性のあるユーザー インターフェイスを提供できます。</span><span class="sxs-lookup"><span data-stu-id="5a489-104">You can use this export feature to present a consistent user interface on multiple computers.</span></span>  
  
 <span data-ttu-id="5a489-105">[登録済みサーバー] のファイルのエクスポートとインポートを順に行うことにより、[登録済みサーバー] の同一サーバーを使用して、複数のコンピューターを簡単に構成できます。</span><span class="sxs-lookup"><span data-stu-id="5a489-105">Exporting and then importing Registered Server files lets you easily configure several computers with the same servers in Registered Servers.</span></span> <span data-ttu-id="5a489-106">これは、複数の場所にあるコンピューターから多数のサーバーを管理する場合、また、経験の少ないユーザーを基本接続設定で構成する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="5a489-106">This is useful when managing a large number of servers from computers in several locations, or when you want to configure a less experienced user with basic connection settings.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5a489-107">SQL Server 認証を使用するサーバー登録では、パスワードをユーザーごとに格納します。</span><span class="sxs-lookup"><span data-stu-id="5a489-107">Server registrations that use SQL Server Authentication store passwords on a per-user basis.</span></span> <span data-ttu-id="5a489-108">サーバー登録のエクスポートとインポートが終了したら、ユーザーは、各サーバーに対して最初の接続時にパスワードを入力する必要があります。これにより、パスワードは登録済みサーバーの一覧に格納されます。</span><span class="sxs-lookup"><span data-stu-id="5a489-108">After exporting and importing the server registrations, users must enter the password for each server the first time they connect, storing the passwords in their lists of registered servers.</span></span> <span data-ttu-id="5a489-109">Windows 認証を使用して登録されたサーバーの場合は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="5a489-109">This is not necessary for servers registered using Windows Authentication.</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-export-registered-server-information"></a><span data-ttu-id="5a489-110">登録済みサーバーの情報をエクスポートするには</span><span class="sxs-lookup"><span data-stu-id="5a489-110">To export registered server information</span></span>  
  
1.  <span data-ttu-id="5a489-111">[登録済みサーバー] で、サーバー グループを右クリックし、 **[エクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a489-111">In Registered Servers, right-click a server group, and then click **Export**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5a489-112">エクスポートできるのは、個別のサーバー、すべての登録済みサーバー ツリー、登録済みサーバー ツリーのサブセットのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="5a489-112">You can export an individual server, all of the registered server tree, or a subset of the registered server tree.</span></span>  
  
2.  <span data-ttu-id="5a489-113">**[登録済みサーバーのエクスポート]** ダイアログ ボックスで、次のオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="5a489-113">In the **Export Registered Servers** dialog box, make the following selections.</span></span>  
  
     <span data-ttu-id="5a489-114">**[サーバー グループ]**</span><span class="sxs-lookup"><span data-stu-id="5a489-114">**Server group**</span></span>  
     <span data-ttu-id="5a489-115">エクスポートするサーバー グループを指定します。</span><span class="sxs-lookup"><span data-stu-id="5a489-115">Specify the server group which will be exported.</span></span> <span data-ttu-id="5a489-116">すべての登録済みサーバー、特定のサーバー グループ内の登録済みサーバー、または 1 つの登録済みサーバーをエクスポート ファイルにエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="5a489-116">Export all registered servers, registered servers in a particular server group, or a single registered server to the export file.</span></span> <span data-ttu-id="5a489-117">エクスポート機能は再帰的です。たとえば、サーバー グループ A にはサーバー グループ B が含まれ、サーバー グループ B にはサーバー グループ C および D が含まれます。サーバー グループ A をエクスポートすると、A、B、C、および D のすべてのエントリがエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="5a489-117">The export functionality is recursive; for example, if server group A contains server group B, and server group B contains server groups C and D, exporting server group A exports all entries in A, B, C, and D.</span></span>  
  
     <span data-ttu-id="5a489-118">サーバー グループには、現在の登録済みサーバー ツリーのサーバー グループだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5a489-118">The server group displays only the server groups of the current registered server tree.</span></span>  
  
     <span data-ttu-id="5a489-119">**[エクスポート ファイル]**</span><span class="sxs-lookup"><span data-stu-id="5a489-119">**Export file**</span></span>  
     <span data-ttu-id="5a489-120">テキスト ボックスにエクスポート ファイルの名前を入力するか、参照ボタン ( **[...]** ) を使用してクライアント コンピューター内のエクスポート ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="5a489-120">Type the name of the export file in the text box or use the Browse button (**...**) to locate an export file on the client computer.</span></span> <span data-ttu-id="5a489-121">既存のファイルを選択した場合は、登録済みサーバー情報がファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="5a489-121">If you select an existing file, the registered server information is appended to the file.</span></span> <span data-ttu-id="5a489-122">.regsrvr 拡張子を使用します。</span><span class="sxs-lookup"><span data-stu-id="5a489-122">Use the .regsrvr extension.</span></span> <span data-ttu-id="5a489-123">登録済みサーバーの情報を他のユーザーまたはコンピューターが利用できるようにする場合は、ネットワーク上にファイルを保存できます。</span><span class="sxs-lookup"><span data-stu-id="5a489-123">If you want your registered server information to be available to other users or another computer, you can save the file on the network.</span></span> <span data-ttu-id="5a489-124">他のユーザーは、そのファイルにアクセスし、一部またはすべての登録済みサーバーの情報をインポートできます。</span><span class="sxs-lookup"><span data-stu-id="5a489-124">Other users can access the file and import part or all of the registered server information.</span></span> <span data-ttu-id="5a489-125">既存のファイルをエクスポート ファイルとして選択した場合、そのファイルの内容はサーバーの登録情報で上書きされます。</span><span class="sxs-lookup"><span data-stu-id="5a489-125">If you select an existing file as your export file, the contents of the file are overwritten with the server registration information.</span></span>  
  
     <span data-ttu-id="5a489-126">**[エクスポート ファイルにユーザー名とパスワードを含めない]**</span><span class="sxs-lookup"><span data-stu-id="5a489-126">**Do not include user names and passwords in the export file**</span></span>  
     <span data-ttu-id="5a489-127">ファイルをエクスポートするときにユーザー名を除外します。</span><span class="sxs-lookup"><span data-stu-id="5a489-127">Exclude user names when exporting the file.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="5a489-128">エクスポート ファイルは暗号化されますが、ユーザー名および SQL&#xA0;Server 認証パスワードがファイルに含まれている場合は、ファイルへのアクセスを慎重に管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a489-128">Although the export files are encrypted, if user names and SQL Server Authentication passwords are included in the file, access to the file should be carefully controlled.</span></span> <span data-ttu-id="5a489-129">したがって、既定では、ユーザー名およびパスワードはエクスポート ファイルから除外されます。</span><span class="sxs-lookup"><span data-stu-id="5a489-129">User names and passwords are therefore excluded from the export file by default.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a489-130">参照</span><span class="sxs-lookup"><span data-stu-id="5a489-130">See Also</span></span>  
 <span data-ttu-id="5a489-131">[登録済みサーバーの情報をインポート &#40;SQL Server Management Studio&#41;](import-registered-server-information-sql-server-management-studio.md) [新しい登録済みサーバー &#40;SQL Server Management Studio を作成&#41;](create-a-new-registered-server-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="5a489-131">[Import Registered Server Information &#40;SQL Server Management Studio&#41;](import-registered-server-information-sql-server-management-studio.md) [Create a New Registered Server &#40;SQL Server Management Studio&#41;](create-a-new-registered-server-sql-server-management-studio.md)</span></span>  
  
  

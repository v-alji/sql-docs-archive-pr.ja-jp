---
title: 登録済みサーバーの情報のインポート
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.importregisteredservers.f1
helpviewer_keywords:
- transferring registered server information
- Registered Servers [SQL Server], importing
- importing registered server information
ms.assetid: cc497a14-1360-4887-b70c-002f042823b6
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f2eddb3b83f73253e977316767f2b930bc8ab9ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737404"
---
# <a name="import-registered-server-information-sql-server-management-studio"></a><span data-ttu-id="c6f62-102">登録済みサーバー情報のインポート (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="c6f62-102">Import Registered Server Information (SQL Server Management Studio)</span></span>
  <span data-ttu-id="c6f62-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]で保存されている登録済みサーバー情報をインポートする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c6f62-103">This topic describes how to import saved registered server information in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="c6f62-104">登録済みサーバー ファイルをエクスポートした後にインポートすることで、[登録済みサーバー] の同じサーバーを使用して、複数のコンピューターを簡単に構成できます。</span><span class="sxs-lookup"><span data-stu-id="c6f62-104">Exporting and then importing registered server files lets you easily configure several computers with the same servers in Registered Servers.</span></span> <span data-ttu-id="c6f62-105">この方法は、複数の場所に配置されているコンピューターから多数のサーバーを管理する場合や、経験の浅いユーザーのために基本的な接続設定を構成する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="c6f62-105">This is useful when managing a large number of servers from computers in several locations, or when you want to configure basic connection settings for a less-experienced user.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c6f62-106">登録済みサーバーの情報を、以前のバージョンの [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にインポートすることはできません。</span><span class="sxs-lookup"><span data-stu-id="c6f62-106">You cannot import registered server information into [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] from earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-import-registered-server-information"></a><span data-ttu-id="c6f62-107">登録済みサーバーの情報をインポートするには</span><span class="sxs-lookup"><span data-stu-id="c6f62-107">To import registered server information</span></span>  
  
1.  <span data-ttu-id="c6f62-108">[登録済みサーバー] で、[登録済みサーバー] ツール バーのサーバーの種類をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6f62-108">In Registered Servers, click the server type on the Registered Servers toolbar.</span></span> <span data-ttu-id="c6f62-109">クリックするサーバーの種類は、登録済みサーバーのエクスポート ファイルの種類と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6f62-109">The server type must be the same as the registered server export file type.</span></span> <span data-ttu-id="c6f62-110">たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の登録済みサーバーの情報をエクスポートした場合、[登録済みサーバー] ツール バーで **[データベース エンジン]** をクリックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6f62-110">For example, if you have exported [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] registered server information, you must click **SQL Server** on the Registered Servers toolbar.</span></span>  
  
2.  <span data-ttu-id="c6f62-111">サーバー グループを右クリックし、 **[インポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6f62-111">Right-click a server group, and select **Import**.</span></span>  
  
3.  <span data-ttu-id="c6f62-112">**[登録済みサーバーのインポート]** ダイアログ ボックスで、インポートする登録済みサーバーのファイルをクリックし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6f62-112">In the **Import Registered Servers** dialog box, select the registered servers file to import, and then click **OK**.</span></span>  
  
     <span data-ttu-id="c6f62-113">**[インポート ファイル]**</span><span class="sxs-lookup"><span data-stu-id="c6f62-113">**Import file**</span></span>  
     <span data-ttu-id="c6f62-114">インポート ファイルの名前をテキスト ボックスに入力します。または、参照ボタン ( **[...]** ) をクリックし、クライアント コンピューター上のインポート ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6f62-114">Type the name of the import file in the text box, or click the Browse button (**...**) to locate the import file on the client computer.</span></span> <span data-ttu-id="c6f62-115">既存のファイルを選択した場合は、登録済みサーバー情報がファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="c6f62-115">If you select an existing file, the registered server information is appended to the file.</span></span> <span data-ttu-id="c6f62-116">あらかじめエクスポートされた登録済みサーバー ファイルだけを、インポート ファイルとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="c6f62-116">The import file can only be a previously exported registered server file.</span></span> <span data-ttu-id="c6f62-117">登録済みサーバー ファイルは、拡張子 .regsrvr を持ちます。</span><span class="sxs-lookup"><span data-stu-id="c6f62-117">Registered server files have a .regsrvr extension.</span></span>  
  
     <span data-ttu-id="c6f62-118">**[インポート先のサーバー グループを選択]**</span><span class="sxs-lookup"><span data-stu-id="c6f62-118">**Select the server group to import to**</span></span>  
     <span data-ttu-id="c6f62-119">ファイル内の登録済みサーバーのエントリのインポート先のルート ノード、または特定のサーバー グループを選択します。</span><span class="sxs-lookup"><span data-stu-id="c6f62-119">Select the root node or a particular server group to which the registered server entries in the file will be imported.</span></span> <span data-ttu-id="c6f62-120">エクスポート ファイルには、すべての登録済みサーバー、特定のサーバー グループ内の登録済みサーバー、または単独の登録済みサーバーをインポートできます。</span><span class="sxs-lookup"><span data-stu-id="c6f62-120">You can import all registered servers, registered servers in a particular server group, or a single registered server to the export file.</span></span> <span data-ttu-id="c6f62-121">インポート機能は再帰的です。たとえば、サーバー グループ A にサーバー グループ B が含まれており、サーバー グループ B にサーバー グループ C および D が含まれている場合、サーバー グループ A をインポートすると、A、B、C、および D 内のすべてのエントリがエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="c6f62-121">The import functionality is recursive; for example, if server group A contains server group B, and server group B contains server groups C and D, importing server group A exports all entries in A, B, C, and D.</span></span>  
  
     <span data-ttu-id="c6f62-122">サーバー グループには、現在の登録済みサーバー ツリーのサーバー グループだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c6f62-122">The server group displays only the server groups of the current registered server tree.</span></span>  
  
     <span data-ttu-id="c6f62-123">既存のサーバー グループまたはサーバーをインポートする場合、既存のサーバーまたはサーバー グループを上書きするかどうかを確認するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c6f62-123">If you select to import an existing server group or server, a message confirms that you want to overwrite the existing server or server group.</span></span>  
  
 <span data-ttu-id="c6f62-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用するサーバー登録は、パスワードをユーザーごとに格納します。</span><span class="sxs-lookup"><span data-stu-id="c6f62-124">Server registrations that use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication store passwords on a per-user basis.</span></span> <span data-ttu-id="c6f62-125">ユーザーは、サーバー登録をインポートした後、それぞれのサーバーに初めて接続するときにパスワードを入力して、登録済みサーバーの一覧にパスワードを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6f62-125">After importing the server registrations, users must enter the password for each server the first time they connect, storing the passwords in their lists of registered servers.</span></span> <span data-ttu-id="c6f62-126">Windows 認証を使用して登録されるサーバーの場合は、この操作は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="c6f62-126">This is not necessary for servers registered through Windows Authentication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6f62-127">参照</span><span class="sxs-lookup"><span data-stu-id="c6f62-127">See Also</span></span>  
 <span data-ttu-id="c6f62-128">[サーバーの登録 &#40;変更 SQL Server Management Studio&#41;](change-a-server-s-registration-sql-server-management-studio.md) [登録済みサーバーの情報のエクスポート &#40;SQL Server Management Studio&#41;](export-registered-server-information-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="c6f62-128">[Change a Server's Registration &#40;SQL Server Management Studio&#41;](change-a-server-s-registration-sql-server-management-studio.md) [Export Registered Server Information &#40;SQL Server Management Studio&#41;](export-registered-server-information-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="c6f62-129">新しい登録済みサーバーの作成 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="c6f62-129">Create a New Registered Server &#40;SQL Server Management Studio&#41;</span></span>](create-a-new-registered-server-sql-server-management-studio.md)  
  
  

---
title: LocalDB | の SQL Server Native Client サポートMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 127569d1-a9f7-49bf-a561-c084986a8871
author: rothja
ms.author: jroth
ms.openlocfilehash: b08ea46e8db1b665280116a439b95748f69d03ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633818"
---
# <a name="sql-server-native-client-support-for-localdb"></a><span data-ttu-id="ff978-102">SQL Server Native Client における LocalDB のサポート</span><span class="sxs-lookup"><span data-stu-id="ff978-102">SQL Server Native Client Support for LocalDB</span></span>
  <span data-ttu-id="ff978-103">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 以降、SQLServer の簡易バージョンである LocalDB を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ff978-103">Beginning in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], a lightweight version of SQL Server, called LocalDB, will be available.</span></span> <span data-ttu-id="ff978-104">ここでは、LocalDB インスタンス内のデータベースに接続する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ff978-104">This topic discusses how to connect to a database in a LocalDB instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff978-105">解説</span><span class="sxs-lookup"><span data-stu-id="ff978-105">Remarks</span></span>  
 <span data-ttu-id="ff978-106">LocalDB のインストール方法や LocalDB インスタンスの構成方法など、LocalDB の詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff978-106">For more information about LocalDB, including how to install LocalDB and configure your LocalDB instance, see:</span></span>  
  
-   [<span data-ttu-id="ff978-107">SQL Server Express LocalDB リファレンス</span><span class="sxs-lookup"><span data-stu-id="ff978-107">SQL Server Express LocalDB Reference</span></span>](../../sql-server-express-localdb-reference.md)  
  
-   [<span data-ttu-id="ff978-108">SQL Server 2014 Express LocalDB</span><span class="sxs-lookup"><span data-stu-id="ff978-108">SQL Server 2014 Express LocalDB</span></span>](../../../database-engine/configure-windows/sql-server-2016-express-localdb.md)  
  
 <span data-ttu-id="ff978-109">要約すると、LocalDB では次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="ff978-109">To summarize, LocalDB allows you to:</span></span>  
  
-   <span data-ttu-id="ff978-110">`sqllocaldb.exe i` を使用して既定のインスタンスの名前を検出できます。</span><span class="sxs-lookup"><span data-stu-id="ff978-110">Use `sqllocaldb.exe i` to discover the name of the default instance.</span></span>  
  
-   <span data-ttu-id="ff978-111">`AttachDBFilename` 接続文字列キーワードを使用して、サーバーをアタッチするデータベース ファイルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="ff978-111">Use the `AttachDBFilename` connection string keyword to specify which database file the server should attach.</span></span> <span data-ttu-id="ff978-112">を使用する場合 `AttachDBFilename` 、データベース接続文字列キーワードでデータベースの名前を指定**Database**しないと、アプリケーションの終了時にデータベースが LocalDB インスタンスから削除されます。</span><span class="sxs-lookup"><span data-stu-id="ff978-112">When using `AttachDBFilename`, if you do not specify the name of the database with the **Database** connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
-   <span data-ttu-id="ff978-113">接続文字列では、次のように LocalDB インスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="ff978-113">Specify a LocalDB instance in your connection string:</span></span>  
  
```  
SERVER=(localdb)\v11.0  
```  
  
 <span data-ttu-id="ff978-114">必要に応じて、sqllocaldb.exe を使用して LocalDB インスタンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ff978-114">If necessary, you can create a LocalDB instance with sqllocaldb.exe.</span></span> <span data-ttu-id="ff978-115">また、sqlcmd.exe を使用して、LocalDB インスタンスのデータベースの追加と変更を実行できます。</span><span class="sxs-lookup"><span data-stu-id="ff978-115">You can also use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="ff978-116">たとえば、「 `sqlcmd -S (localdb)\v11.0` 」のように入力します。</span><span class="sxs-lookup"><span data-stu-id="ff978-116">For example, `sqlcmd -S (localdb)\v11.0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff978-117">参照</span><span class="sxs-lookup"><span data-stu-id="ff978-117">See Also</span></span>  
 [<span data-ttu-id="ff978-118">SQL Server Native Client の機能</span><span class="sxs-lookup"><span data-stu-id="ff978-118">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  

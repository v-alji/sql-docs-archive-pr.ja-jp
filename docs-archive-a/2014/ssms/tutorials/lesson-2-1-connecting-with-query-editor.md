---
title: クエリ エディターとの接続 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 48725f54-a7b6-4b79-948e-965c1fe4eef1
author: stevestein
ms.author: sstein
ms.openlocfilehash: b50783450dfb9516c78a465806ee322d7a575377
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642470"
---
# <a name="connecting-with-query-editor"></a><span data-ttu-id="08f3c-102">クエリ エディターとの接続</span><span class="sxs-lookup"><span data-stu-id="08f3c-102">Connecting with Query Editor</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="08f3c-103">では、サーバーから切断されていてもコードの記述と編集を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="08f3c-103">permits you to write or edit code while disconnected from the server.</span></span> <span data-ttu-id="08f3c-104">この機能は、サーバーを利用できない場合、またはサーバーやネットワークの限られたリソースを節約したい場合に有効です。</span><span class="sxs-lookup"><span data-stu-id="08f3c-104">This can be useful when the server is not available or when you want to conserve scarce server or network resources.</span></span> <span data-ttu-id="08f3c-105">さらに、新しいクエリ エディター ウィンドウを開いたり、コードを再入力したりしなくても、クエリ エディターの接続を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新しいインスタンスに変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="08f3c-105">You can also change the connection of Query Editor to a new instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without opening a new Query Editor window or retyping your code.</span></span>  
  
## <a name="coding-offline"></a><span data-ttu-id="08f3c-106">オフラインでのコーディング</span><span class="sxs-lookup"><span data-stu-id="08f3c-106">Coding Offline</span></span>  
  
#### <a name="to-write-code-offline-and-then-connect-to-different-servers"></a><span data-ttu-id="08f3c-107">コードをオフラインで記述した後、別のサーバーに接続するには</span><span class="sxs-lookup"><span data-stu-id="08f3c-107">To write code offline and then connect to different servers</span></span>  
  
1.  <span data-ttu-id="08f3c-108">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] のツール バーの **[データベース エンジン クエリ]** をクリックして、クエリ エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="08f3c-108">On the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] toolbar, click **Database Engine Query** to open the Query Editor.</span></span>  
  
2.  <span data-ttu-id="08f3c-109">**[データベース エンジンへの接続]** ダイアログ ボックスで、 **[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08f3c-109">In the **Connect to Database Engine** dialog box, click **Cancel**.</span></span> <span data-ttu-id="08f3c-110">クエリ エディターを開きます。クエリ エディターのタイトル バーから、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続されていないことがわかります。</span><span class="sxs-lookup"><span data-stu-id="08f3c-110">The Query Editor opens, and the title bar for the Query Editor indicates that you are not connected to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="08f3c-111">コード ペインに次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="08f3c-111">In the code pane, type the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    SELECT * FROM Production.Product;  
    GO  
    ```  
  
     <span data-ttu-id="08f3c-112">この時点で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [接続] **、**[実行] **、**[解析] **、または**[推定実行プランの表示] **をクリックすることにより、** のインスタンスに接続できます。これらのオプションは、 **[クエリ]** メニュー、クエリ エディターのツール バー、または [クエリ エディター] ウィンドウを右クリックすると表示されるショートカット メニューから実行できます。</span><span class="sxs-lookup"><span data-stu-id="08f3c-112">At this point you can connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by clicking **Connect**, **Execute**, **Parse**, or **Display Estimated Execution Plan**, all of which are available from either the **Query** menu, the Query Editor toolbar, or from the shortcut menu when you right-click in the Query Editor window.</span></span> <span data-ttu-id="08f3c-113">この実習ではツール バーを使用します。</span><span class="sxs-lookup"><span data-stu-id="08f3c-113">For this practice, we'll use the toolbar.</span></span>  
  
4.  <span data-ttu-id="08f3c-114">ツール バーの **[実行]** ボタンをクリックします。 **[データベース エンジンへの接続]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="08f3c-114">On the toolbar, click the **Execute** button to open the **Connect to Database Engine** dialog box.</span></span>  
  
5.  <span data-ttu-id="08f3c-115">**[サーバー名]** ボックスにサーバー名を入力し、 **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08f3c-115">In the **Server name** text box, type your server name, and then click **Options**.</span></span>  
  
6.  <span data-ttu-id="08f3c-116">**[接続プロパティ]** タブで、 **[データベースへの接続]** ボックスの一覧から [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] を選択し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08f3c-116">On the **Connection Properties** tab, in the **Connect to database** list, browse the server to select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] and then click **Connect**.</span></span>  
  
7.  <span data-ttu-id="08f3c-117">同じサーバーに接続する別のクエリ エディター ウィンドウを開くには、ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08f3c-117">To open another Query Editor window with the same connection, on the toolbar click **New Query**.</span></span>  
  
8.  <span data-ttu-id="08f3c-118">接続先を変更するには、クエリ エディター ウィンドウを右クリックし、 **[接続]** をポイントして、 **[接続の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08f3c-118">To change connections, right-click in the Query Editor window, point to **Connection**, and then click **Change Connection**.</span></span>  
  
9. <span data-ttu-id="08f3c-119">**[サーバーへの接続]** ダイアログ ボックスで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の別の有効なインスタンスを選択し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08f3c-119">In the **Connect to SQL Server** dialog box, select another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] if available, and then click **Connect**.</span></span>  
  
 <span data-ttu-id="08f3c-120">クエリ エディターの新機能により、複数のサーバーで同じコードを容易に実行できます。</span><span class="sxs-lookup"><span data-stu-id="08f3c-120">This new feature of Query Editor enables you to easily run the same code on several servers.</span></span> <span data-ttu-id="08f3c-121">類似する複数のサーバーの保守を行う場合などは、この機能を使用すると便利です。</span><span class="sxs-lookup"><span data-stu-id="08f3c-121">This may be useful for maintenance actions involving similar servers.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="08f3c-122">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="08f3c-122">Next Task in Lesson</span></span>  
 [<span data-ttu-id="08f3c-123">インデントの追加</span><span class="sxs-lookup"><span data-stu-id="08f3c-123">Adding Indentation</span></span>](lesson-2-2-adding-indentation.md)  
  
  

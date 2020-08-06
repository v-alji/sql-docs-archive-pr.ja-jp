---
title: '手順 3: OLE DB 接続マネージャーの追加と構成 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e7b74cba-a0e5-4478-af12-3f81b9484e9e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3bc4c885ce6c39c72031dd3b528a769cd47ac8f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641105"
---
# <a name="step-3-adding-and-configuring-an-ole-db-connection-manager"></a><span data-ttu-id="63757-102">手順 3:OLE DB 接続マネージャーの追加と構成</span><span class="sxs-lookup"><span data-stu-id="63757-102">Step 3: Adding and Configuring an OLE DB Connection Manager</span></span>
  <span data-ttu-id="63757-103">前の実習では、データ ソースに接続するためのフラット ファイル接続マネージャーを追加しました。次は、データの変換先に接続するための OLE DB 接続マネージャーを追加します。</span><span class="sxs-lookup"><span data-stu-id="63757-103">After you have added a Flat File connection manager to connect to the data source, the next task is to add an OLE DB connection manager to connect to the destination.</span></span> <span data-ttu-id="63757-104">パッケージに OLE DB 接続マネージャーを追加すれば、OLE DB 対応のデータ ソースからデータを抽出したり、OLE DB 対応のデータ ソースへデータを読み込んだりできるようになります。</span><span class="sxs-lookup"><span data-stu-id="63757-104">An OLE DB connection manager enables a package to extract data from or load data into any OLE DB-compliant data source.</span></span> <span data-ttu-id="63757-105">OLE DB 接続マネージャーでは、接続に必要なサーバー、認証方法、既定のデータベースを指定できます。</span><span class="sxs-lookup"><span data-stu-id="63757-105">Using the OLE DB Connection manager, you can specify the server, the authentication method, and the default database for the connection.</span></span>  
  
 <span data-ttu-id="63757-106">このレッスンでは、Windows 認証を使用して **AdventureWorksDB2012**のローカル インスタンスに接続する OLE DB 接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="63757-106">In this lesson, you will create an OLE DB connection manager that uses Windows Authentication to connect to the local instance of **AdventureWorksDB2012**.</span></span> <span data-ttu-id="63757-107">参照変換や OLE DB 変換先など、このチュートリアルで後ほど作成するその他のコンポーネントも、ここで作成する OLE DB 接続マネージャーを参照します。</span><span class="sxs-lookup"><span data-stu-id="63757-107">The OLE DB connection manager that you create will also be referenced by other components that you will create later in this tutorial, such as the Lookup transformation and the OLE DB destination.</span></span>  
  
### <a name="to-add-and-configure-an-ole-db-connection-manager-to-the-ssis-package"></a><span data-ttu-id="63757-108">SSIS パッケージに OLE DB 接続マネージャーを追加して構成するには</span><span class="sxs-lookup"><span data-stu-id="63757-108">To add and configure an OLE DB Connection Manager to the SSIS package</span></span>  
  
1.  <span data-ttu-id="63757-109">**[接続マネージャー]** 領域内を右クリックし、 **[新しい OLE DB 接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="63757-109">Right-click anywhere in the **Connection Managers** area, and then click **New OLE DB Connection**.</span></span>  
  
2.  <span data-ttu-id="63757-110">**[OLE DB 接続マネージャーの構成]** ダイアログ ボックスで、 **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="63757-110">In the **Configure OLE DB Connection Manager** dialog box, click **New**.</span></span>  
  
3.  <span data-ttu-id="63757-111">**[サーバー名]** に「 **localhost**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="63757-111">For **Server name**, enter **localhost**.</span></span>  
  
     <span data-ttu-id="63757-112">サーバー名に localhost という名前を使用すると、接続マネージャーは、ローカル コンピューター上の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の既定のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="63757-112">When you specify localhost as the server name, the connection manager connects to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the local computer.</span></span> <span data-ttu-id="63757-113">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のリモート インスタンスを使用するには、localhost ではなく、接続先のサーバー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="63757-113">To use a remote instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], replace localhost with the name of the server to which you want to connect.</span></span>  
  
4.  <span data-ttu-id="63757-114">**[サーバーにログオンする]** で、 **[Windows 認証を使用する]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="63757-114">In the **Log on to the server** group, verify that **Use Windows Authentication** is selected.</span></span>  
  
5.  <span data-ttu-id="63757-115">[**データベースへの接続**] グループの **[データベース名の選択または入力**] ボックスに、「」と入力するか、またはを選択し `AdventureWorksDW2012` ます。</span><span class="sxs-lookup"><span data-stu-id="63757-115">In the **Connect to a database** group, in the **Select or enter a database name** box, type or select `AdventureWorksDW2012`.</span></span>  
  
6.  <span data-ttu-id="63757-116">**[接続テスト]** をクリックし、指定した接続設定が有効であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="63757-116">Click **Test Connection** to verify that the connection settings you have specified are valid.</span></span>  
  
7.  <span data-ttu-id="63757-117">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="63757-117">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="63757-118">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="63757-118">Click **OK**.</span></span>  
  
9. <span data-ttu-id="63757-119">**[OLE DB 接続マネージャーの構成]** ダイアログ ボックスの **[データ接続]** ペインで、 **localhost.AdventureWorksDW2012** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="63757-119">In the **Data Connections** pane of the **Configure OLE DB Connection Manager** dialog box, verify that **localhost.AdventureWorksDW2012** is selected.</span></span>  
  
10. <span data-ttu-id="63757-120">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="63757-120">Click **OK**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="63757-121">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="63757-121">Next Task in Lesson</span></span>  
 [<span data-ttu-id="63757-122">手順 4:パッケージへのデータ フロー タスクの追加</span><span class="sxs-lookup"><span data-stu-id="63757-122">Step 4: Adding a Data Flow Task to the Package</span></span>](lesson-1-4-adding-a-data-flow-task-to-the-package.md)  
  
## <a name="see-also"></a><span data-ttu-id="63757-123">参照</span><span class="sxs-lookup"><span data-stu-id="63757-123">See Also</span></span>  
 [<span data-ttu-id="63757-124">OLE DB 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="63757-124">OLE DB Connection Manager</span></span>](connection-manager/ole-db-connection-manager.md)  
  
  

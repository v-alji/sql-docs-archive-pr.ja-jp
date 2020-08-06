---
title: '[サーバーへの接続]([追加の接続パラメーター] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttoserver.options.registeredservers.f1
ms.assetid: ba34b01a-6289-4eb8-8341-fa3d9ec87b3f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5c6a23df6a6b9ea324d54fd270f5aa2269471ed8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645835"
---
# <a name="connect-to-server-additional-connection-parameters-page"></a><span data-ttu-id="516ef-102">[サーバーへの接続] ([追加の接続パラメーター] ページ)</span><span class="sxs-lookup"><span data-stu-id="516ef-102">Connect to Server (Additional Connection Parameters Page)</span></span>
  <span data-ttu-id="516ef-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] の **[接続先]** ダイアログ ボックスには、オプションとして最も一般的な接続文字列値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="516ef-103">The **Connect to** dialog box of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] presents the most common connection string values as options.</span></span> <span data-ttu-id="516ef-104">**[追加の接続パラメーター]** ページを使用すると、接続文字列に接続パラメーターをさらに追加できます。</span><span class="sxs-lookup"><span data-stu-id="516ef-104">Use the **Additional Connection Parameters** page to add more connection parameters to the connection string.</span></span>  
  
-   <span data-ttu-id="516ef-105">追加の接続パラメーターには、任意の ODBC 接続パラメーターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="516ef-105">Additional connection parameters can be any ODBC connection parameter.</span></span>  
  
-   <span data-ttu-id="516ef-106">追加の接続パラメーターは、 **;parameter1=value1;parameter2=value2**という形式で追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="516ef-106">Additional connection parameters should be added in the format **;parameter1=value1;parameter2=value2**.</span></span>  
  
-   <span data-ttu-id="516ef-107">**[追加の接続パラメーター]** ページを使用して追加したパラメーターは、 **[接続先]** ダイアログ ボックスのオプションを使用して選択したパラメーターに追加されます。</span><span class="sxs-lookup"><span data-stu-id="516ef-107">Parameters added using the **Additional Connection Parameters** page are added to the parameters selected using the **Connect to** dialog box options.</span></span>  
  
-   <span data-ttu-id="516ef-108">指定した各パラメーターの最後のインスタンスは、そのパラメーターの前のインスタンスをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="516ef-108">The last instance of each parameter provided overrides any previous instances of the parameter.</span></span> <span data-ttu-id="516ef-109">**[追加の接続パラメーター]** ページを使用して追加したパラメーターは、 **[ログイン]** タブまたは **[接続プロパティ]** タブで指定したパラメーターより優先されます。</span><span class="sxs-lookup"><span data-stu-id="516ef-109">Parameters added using the **Additional Connection Parameters** page follow and replace the parameters provided in the **Login** or **Connection Properties** tabs.</span></span> <span data-ttu-id="516ef-110">たとえば、 **[ログイン]** タブの **[サーバー名]** で「 **SERVER1**」と指定し、 **[追加の接続パラメーター]** ページで「 **;SERVER=SERVER2**」と指定した場合、 **SERVER2**に接続されます。</span><span class="sxs-lookup"><span data-stu-id="516ef-110">For example, if the **Login** tab provides **SERVER1** as the **Server name**, and the **Additional Connection Parameters** page contains **;SERVER=SERVER2**, the connection will be made to **SERVER2**.</span></span>  
  
-   <span data-ttu-id="516ef-111">**[追加の接続パラメーター]** ページで追加したパラメーターは、常にプレーン テキストとして渡されます。</span><span class="sxs-lookup"><span data-stu-id="516ef-111">Parameters added using the **Additional Connection Parameters** page are always passed as plain text.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="516ef-112">**[追加の接続パラメーター]** ページにはログイン資格情報やパスワードを含めないでください。</span><span class="sxs-lookup"><span data-stu-id="516ef-112">Do not include login credentials and passwords in the **Additional Connection Parameters** page.</span></span> <span data-ttu-id="516ef-113">このダイアログ ボックスで指定したパラメーターは、ネットワーク経由で渡されるときに暗号化されません。</span><span class="sxs-lookup"><span data-stu-id="516ef-113">They will not be encrypted when they are passed across the network.</span></span> <span data-ttu-id="516ef-114">代わりに **[ログイン]** タブを使用してください。</span><span class="sxs-lookup"><span data-stu-id="516ef-114">Use the **Login** tab instead.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="516ef-115">タスク一覧</span><span class="sxs-lookup"><span data-stu-id="516ef-115">Task List</span></span>  
  
### <a name="to-show-the-additional-connection-parameters-page"></a><span data-ttu-id="516ef-116">[追加の接続パラメーター] ページを表示するには</span><span class="sxs-lookup"><span data-stu-id="516ef-116">To show the Additional Connection Parameters page</span></span>  
  
1.  <span data-ttu-id="516ef-117">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]で、 **[クエリ]** メニューの **[接続]** をポイントし、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="516ef-117">In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], on the **Query** menu, point to **Connection**, and then click **Connect**.</span></span>  
  
2.  <span data-ttu-id="516ef-118">**[接続先]** ダイアログ ボックスで、 **[オプション]** をクリックし、 **[追加の接続パラメーター]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="516ef-118">In the **Connect to** dialog box, click **Options**, and then click the **Additional Connection Parameters** tab.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="516ef-119">例</span><span class="sxs-lookup"><span data-stu-id="516ef-119">Examples</span></span>  
  
### <a name="example-a-connecting-to-the-database-engine"></a><span data-ttu-id="516ef-120">例 A: データベース エンジンへの接続</span><span class="sxs-lookup"><span data-stu-id="516ef-120">Example A: Connecting to the Database Engine</span></span>  
 <span data-ttu-id="516ef-121">ACCOUNTING というサーバーの [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] データベースに接続するには、 **[追加の接続パラメーター]** ページに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="516ef-121">To connect to the [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] database on a server named ACCOUNTING, enter the following in the **Additional connection parameters** page:</span></span>  
  
```  
;SERVER=ACCOUNTING;DATABASE=AdventureWorks2012  
```  
  
### <a name="example-b-connecting-to-analysis-services"></a><span data-ttu-id="516ef-122">例 B: Analysis Services への接続</span><span class="sxs-lookup"><span data-stu-id="516ef-122">Example B: Connecting to Analysis Services</span></span>  
 <span data-ttu-id="516ef-123">分析サーバーに接続し、通知をリッスンするすべてのパーティションに対するクエリが (キャッシュをバイパスして) リアルタイムで実行されるようにして、書き戻しのタイムアウト値を 5 に設定するには、 **[追加の接続パラメーター]** ページに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="516ef-123">To connect to the Analysis Servers and cause all the partitions listening for notifications to be queried as real time (bypassing caching), and to set the writeback time out value to 5, enter the following in the **Additional connection parameters** page:</span></span>  
  
```  
;Real Time Olap=TRUE;Writeback Timeout=5  
```  
  
  

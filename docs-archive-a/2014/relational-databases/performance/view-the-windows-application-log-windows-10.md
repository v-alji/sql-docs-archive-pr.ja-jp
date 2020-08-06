---
title: Windows アプリケーション ログの表示 (Windows) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- viewing logs
- application logs [SQL Server]
- logs [SQL Server], application
- monitoring Windows NT application log [SQL Server]
- Windows NT application logs [SQL Server]
- displaying logs
- monitoring [SQL Server], events
- logs [SQL Server], viewing
ms.assetid: 168a6c6e-12df-46a9-9904-55d63ca8fe14
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1255e95833d9fc56abd1700f5acb0d2f49ebf77c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715229"
---
# <a name="view-the-windows-application-log-windows"></a><span data-ttu-id="cbfeb-102">Windows アプリケーション ログの表示 (Windows)</span><span class="sxs-lookup"><span data-stu-id="cbfeb-102">View the Windows Application Log (Windows)</span></span>
  <span data-ttu-id="cbfeb-103">Windows アプリケーション ログを使用するように [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が構成されている場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各セッションで新しいイベントがそのログに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="cbfeb-103">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured to use the Windows application log, each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] session writes new events to that log.</span></span> <span data-ttu-id="cbfeb-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログとは異なり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを開始するたびに新しいアプリケーション ログが作成されることはありません。</span><span class="sxs-lookup"><span data-stu-id="cbfeb-104">Unlike the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, a new application log is not created each time you start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="to-view-the-windows-application-log"></a><span data-ttu-id="cbfeb-105">Windows アプリケーション ログを表示するには</span><span class="sxs-lookup"><span data-stu-id="cbfeb-105">To view the Windows application log</span></span>  
  
1.  <span data-ttu-id="cbfeb-106">**[スタート]** ボタンをクリックし、 **[すべてのプログラム]**、 **[管理ツール]** の順にポイントして、 **[イベント ビューアー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cbfeb-106">On the **Start** menu, point to **All Programs**, point to **Administrative Tools**, and then click **Event Viewer**.</span></span>  
  
2.  <span data-ttu-id="cbfeb-107">イベント ビューアーで **[アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cbfeb-107">In Event Viewer, click **Application**.</span></span>  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cbfeb-108">イベントは、 **[ソース]** 列に **MSSQLSERVER** (名前付きインスタンスの場合は **MSSQL$** _<instance_name>_ ) と表示されます。</span><span class="sxs-lookup"><span data-stu-id="cbfeb-108">events are identified by the entry **MSSQLSERVER** (named instances are identified with **MSSQL$**_<instance_name>_) in the **Source** column.</span></span> <span data-ttu-id="cbfeb-109">SQL Server エージェントのイベントは SQLSERVERAGENT エントリで識別されます ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の名前付きインスタンスの場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのイベントは **SQLAgent$** \<*instance_name*> で識別されます)。</span><span class="sxs-lookup"><span data-stu-id="cbfeb-109">SQL Server Agent events are identified by the entry SQLSERVERAGENT (for named instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent events are identified with **SQLAgent$**\<*instance_name*>).</span></span> <span data-ttu-id="cbfeb-110">Microsoft Search サービスのイベントは " **Microsoft Search**" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="cbfeb-110">Microsoft Search service events are identified by the entry **Microsoft Search**.</span></span>  
  
4.  <span data-ttu-id="cbfeb-111">別のコンピューターのログを表示するには、 **[イベント ビューアー]** を右クリックし、 **[別のコンピューターへ接続]** をクリックします。次に、 **[コンピューターの選択]** ダイアログ ボックスで必要な項目を設定します。</span><span class="sxs-lookup"><span data-stu-id="cbfeb-111">To view the log of a different computer, right-click **Event Viewer**, click **Connect to another computer,** and complete the **Select Computer**dialog box.</span></span>  
  
5.  <span data-ttu-id="cbfeb-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のイベントのみを表示する場合は、 **[表示]** メニューの **[フィルター]** をクリックし、 **[イベント ソース]** ボックスの一覧で **[MSSQLSERVER]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cbfeb-112">Optionally, to display only [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events, on the **View** menu click **Filter**, and in the **Event source** list, select **MSSQLSERVER**.</span></span> <span data-ttu-id="cbfeb-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのイベントのみを表示するには、 **[イベント ソース]** ボックスの一覧で **[SQLSERVERAGENT]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cbfeb-113">To view only [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent events, instead select **SQLSERVERAGENT** in the **Event source** list.</span></span>  
  
6.  <span data-ttu-id="cbfeb-114">イベントについての詳細情報を表示するには、イベントをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="cbfeb-114">To view more information about an event, double-click the event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbfeb-115">参照</span><span class="sxs-lookup"><span data-stu-id="cbfeb-115">See Also</span></span>  
 [<span data-ttu-id="cbfeb-116">SQL Server エラー ログの表示 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="cbfeb-116">View the SQL Server Error Log &#40;SQL Server Management Studio&#41;</span></span>](../../ssms/sql-server-management-studio-ssms.md)  
  
  

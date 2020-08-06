---
title: サーバーのプロパティ ([実行] ページ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.execution.f1
ms.assetid: 53b77db1-b013-4dac-82dd-30c0de276639
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f0ec8725a0cec9e15cb6d8402f8d654320c38471
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641976"
---
# <a name="server-properties-execution-page"></a><span data-ttu-id="c311f-102">[サーバーのプロパティ] [実行] ページ)</span><span class="sxs-lookup"><span data-stu-id="c311f-102">Server Properties (Execution Page)</span></span>
  <span data-ttu-id="c311f-103">このページを使用すると、レポート実行のタイムアウト値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="c311f-103">Use this page to set a timeout value for report execution.</span></span> <span data-ttu-id="c311f-104">この値は、現在のレポート サーバー インスタンスによって処理されるすべてのレポートに適用されます。</span><span class="sxs-lookup"><span data-stu-id="c311f-104">This value applies to all reports that are processed by the current report server instance.</span></span> <span data-ttu-id="c311f-105">この設定は、レポートごとにオーバーライドすることができます。</span><span class="sxs-lookup"><span data-stu-id="c311f-105">You can override this value for individual reports.</span></span> <span data-ttu-id="c311f-106">レポート サーバーで行われるすべてのレポート処理の時間に加え、レポート内で使用されるデータをレポート サーバーが取得するときにデータベース サーバーで実行されるクエリ処理に対応する時間も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c311f-106">The value you specify must accommodate all report processing that occurs on the report server, plus query processing performed on the database server when the report server retrieves data that is used in the report.</span></span>  
  
 <span data-ttu-id="c311f-107">このページを開くには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を起動してレポート サーバー インスタンスに接続し、レポート サーバー名を右クリックして **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c311f-107">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server instance, right-click the report server name, and select **Properties**.</span></span> <span data-ttu-id="c311f-108">**[実行]** をクリックするとこのページが開きます。</span><span class="sxs-lookup"><span data-stu-id="c311f-108">Click **Execution** to open this page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c311f-109">オプション</span><span class="sxs-lookup"><span data-stu-id="c311f-109">Options</span></span>  
 <span data-ttu-id="c311f-110">**[レポートの実行をタイムアウトしない]**</span><span class="sxs-lookup"><span data-stu-id="c311f-110">**Do not timeout report execution**</span></span>  
 <span data-ttu-id="c311f-111">レポート サーバーでレポート処理が完了するまでの時間を制限しないようにします。</span><span class="sxs-lookup"><span data-stu-id="c311f-111">Allow a report server unlimited time to complete report processing.</span></span>  
  
 <span data-ttu-id="c311f-112">**[レポートの実行を次の秒数に制限する]**</span><span class="sxs-lookup"><span data-stu-id="c311f-112">**Limit report execution to the following number of seconds**</span></span>  
 <span data-ttu-id="c311f-113">レポート実行の時間制限を設定します。</span><span class="sxs-lookup"><span data-stu-id="c311f-113">Set a time constraint on report execution.</span></span> <span data-ttu-id="c311f-114">時間はレポートが要求されたときから測定されます。</span><span class="sxs-lookup"><span data-stu-id="c311f-114">The time period starts when the report is requested.</span></span> <span data-ttu-id="c311f-115">レポートが完全に処理される前に制限時間に到達した場合、レポート サーバーは、処理および外部データ ソースに対するインプロセス クエリをすべて取り消します。</span><span class="sxs-lookup"><span data-stu-id="c311f-115">If the time period ends before the report is fully processed, the report server cancels the process and any in-process queries to external data sources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c311f-116">参照</span><span class="sxs-lookup"><span data-stu-id="c311f-116">See Also</span></span>  
 <span data-ttu-id="c311f-117">[レポート サーバーのプロパティを設定する (Management Studio)](set-report-server-properties-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="c311f-117">[Set Report Server Properties &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span></span>  
 <span data-ttu-id="c311f-118">[Management Studio でレポート サーバーに接続する](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="c311f-118">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="c311f-119">[レポート処理プロパティの設定](../report-server/set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="c311f-119">[Set Report Processing Properties](../report-server/set-report-processing-properties.md) </span></span>  
 <span data-ttu-id="c311f-120">[レポートおよび共有データセット処理のタイムアウト値の設定 &#40;SSRS&#41;](../report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c311f-120">[Setting Time-out Values for Report and Shared Dataset Processing &#40;SSRS&#41;](../report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md) </span></span>  
 [<span data-ttu-id="c311f-121">Management Studio のレポート サーバーの F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="c311f-121">Report Server in Management Studio F1 Help</span></span>](report-server-in-management-studio-f1-help.md)  
  
  

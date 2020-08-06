---
title: 共有データセットのキャッシュ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c2d8c81a-da1e-4a8a-9845-fff9a0903d24
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d4757d82425368efcb6a0a555c6cfe1deacf48c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642571"
---
# <a name="cache-a-shared-dataset"></a><span data-ttu-id="5c962-102">共有データセットのキャッシュ</span><span class="sxs-lookup"><span data-stu-id="5c962-102">Cache a Shared Dataset</span></span>
  <span data-ttu-id="5c962-103">パフォーマンスを向上させる方法の 1 つに、共有データセットのキャッシュ プロパティを構成するという方法があります。</span><span class="sxs-lookup"><span data-stu-id="5c962-103">One way to improve performance is to configure caching properties for a shared dataset.</span></span> <span data-ttu-id="5c962-104">共有データセットをキャッシュに格納した場合、クエリ結果のコピーが指定の時間、保存されます。</span><span class="sxs-lookup"><span data-stu-id="5c962-104">When a shared dataset is cached, a copy of the query results is saved for a specified period of time.</span></span> <span data-ttu-id="5c962-105">共有データセットを使用するレポートを要求した 1 人目のユーザーは、クエリ結果とすべての処理が完了しないとレポートを閲覧できません。</span><span class="sxs-lookup"><span data-stu-id="5c962-105">The first user who requests a report that uses the shared dataset must wait for the query results and all processing to complete before viewing the report.</span></span> <span data-ttu-id="5c962-106">それ以降、同じレポートを要求したユーザーは、キャッシュの保持時間内であれば、クエリと処理が既に完了しているため、すぐにレポートを閲覧できます。</span><span class="sxs-lookup"><span data-stu-id="5c962-106">Subsequent users who request the report within the caching period will experience improved performance because the query and processing has already occurred.</span></span> <span data-ttu-id="5c962-107">キャッシュ更新計画を指定してクエリを実行し、指定したキャッシュ有効期限まで結果をキャッシュしておくこともできます。</span><span class="sxs-lookup"><span data-stu-id="5c962-107">You can also specify a cache refresh plan to run the query and cache the results until the specified cache expiration.</span></span>  
  
 <span data-ttu-id="5c962-108">共有データセットまたはキャッシュ更新計画に基づいてレポートを実行するユーザーは、クエリ キャッシュを作成します。どちらの場合も、キャッシュ有効期限オプションに基づいてキャッシュを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5c962-108">Users running reports based on a shared dataset or cache refresh plans create the query cache and in both cases, the cache is available based on the cache expiration options.</span></span>  
  
 <span data-ttu-id="5c962-109">キャッシュできる共有データセットの種類には制限があります。</span><span class="sxs-lookup"><span data-stu-id="5c962-109">There are restrictions on the types of shared datasets that you can cache.</span></span> <span data-ttu-id="5c962-110">たとえば、データがユーザー ID によって異なる場合や、レポートを要求したユーザーのセキュリティ トークンを使ってデータが取得される場合、クエリ結果をキャッシュすることはできません。</span><span class="sxs-lookup"><span data-stu-id="5c962-110">For example, the query results cannot be cached if the data varies based on the user identity or if data is retrieved using the security token of the user who requests the report.</span></span> <span data-ttu-id="5c962-111">詳細については、「[共有データセットのキャッシュ &#40;SSRS&#41;](cache-shared-datasets-ssrs.md)」と「[レポートのキャッシュ &#40;SSRS&#41;](caching-reports-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c962-111">For more information, see [Cache Shared Datasets &#40;SSRS&#41;](cache-shared-datasets-ssrs.md) and [Caching Reports &#40;SSRS&#41;](caching-reports-ssrs.md).</span></span>  
  
### <a name="to-schedule-the-expiration-of-a-cached-report"></a><span data-ttu-id="5c962-112">キャッシュされたレポートの有効期限をスケジュールするには</span><span class="sxs-lookup"><span data-stu-id="5c962-112">To schedule the expiration of a cached report</span></span>  
  
1.  <span data-ttu-id="5c962-113">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md) を開始します。</span><span class="sxs-lookup"><span data-stu-id="5c962-113">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="5c962-114">レポート マネージャーで、キャッシュ プロパティを設定する共有データセットに移動し、アイテムの上にマウス ポインターを移動して、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c962-114">In Report Manager, navigate to the shared dataset for which you want to set caching properties, hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="5c962-115">ドロップダウン メニューの **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c962-115">In the drop-down menu, click **Manage**.</span></span>  
  
4.  <span data-ttu-id="5c962-116">左フレームの **[キャッシュ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c962-116">In the left frame, click **Caching**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5c962-117">**「共有データセットを実行するための資格情報が保存されていません」** というエラーが発生する場合は、共有データセットのキャッシュ オプションが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="5c962-117">If you see the error **Credentials used to run the shared dataset are not stored**, the cache shared dataset option will be disabled.</span></span> <span data-ttu-id="5c962-118">資格情報を保存するようにデータ ソースを変更するか、または資格情報が保存されている別のデータ ソースを使用するように共有データセットを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5c962-118">You need modify the data source to store credentials or modify the shared dataset to use a different data source that does store credentials.</span></span>  
  
5.  <span data-ttu-id="5c962-119">**[共有データセットのキャッシュ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c962-119">Select **Cache share dataset**.</span></span>  
  
6.  <span data-ttu-id="5c962-120">30 分後にキャッシュが期限切れになるようにオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="5c962-120">Select the option to expire the cache after 30 minutes.</span></span> <span data-ttu-id="5c962-121">キャッシュが指定のスケジュールに従って期限切れになるように選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="5c962-121">You can also choose for the cache to expire on a specified schedule.</span></span>  
  
7.  <span data-ttu-id="5c962-122">**[Apply]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c962-122">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c962-123">参照</span><span class="sxs-lookup"><span data-stu-id="5c962-123">See Also</span></span>  
 [<span data-ttu-id="5c962-124">共有データセットを管理する</span><span class="sxs-lookup"><span data-stu-id="5c962-124">Manage Shared Datasets</span></span>](../report-data/manage-shared-datasets.md)  
  
  

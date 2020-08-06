---
title: カタログ アイテムの削除 (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.deleteitems.f1
ms.assetid: b0599e01-6dc3-4484-80d4-022a412e0ebd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d2a1824f2611165c9ae891fcb702418244f3621e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639897"
---
# <a name="delete-catalog-items-management-studio"></a><span data-ttu-id="a4a26-102">カタログ アイテムの削除 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="a4a26-102">Delete Catalog Items (Management Studio)</span></span>
  <span data-ttu-id="a4a26-103">このページを使用すると、共有スケジュールとロール定義を削除できます。</span><span class="sxs-lookup"><span data-stu-id="a4a26-103">Use this page to delete shared schedules and role definitions.</span></span>  
  
 <span data-ttu-id="a4a26-104">複数のレポートおよびサブスクリプションによって使用される共有スケジュールを削除した場合、以前にその共有スケジュールを使用していたレポートおよびサブスクリプションごとに別個のスケジュールが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a4a26-104">If you delete a shared schedule that is used by multiple reports and subscriptions, the report server will create individual schedules for each report and subscription that previously used the shared schedule.</span></span> <span data-ttu-id="a4a26-105">新たに作成される各スケジュールには、共有スケジュールで指定されていた日付、時刻、および定期的なパターンが保持されます。</span><span class="sxs-lookup"><span data-stu-id="a4a26-105">Each new individual schedule will contain the date, time, and recurrence pattern that was specified in the shared schedule.</span></span> <span data-ttu-id="a4a26-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] には、個々のスケジュールを一元管理する手段は存在しません。</span><span class="sxs-lookup"><span data-stu-id="a4a26-106">Note that [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] does not provide central management of individual schedules.</span></span> <span data-ttu-id="a4a26-107">共有スケジュールを削除した場合、それ以降は、各アイテムのスケジュール情報を個別に管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4a26-107">If you delete a shared schedule, you will now need to maintain the schedule information for each individual item.</span></span> <span data-ttu-id="a4a26-108">共有スケジュールを削除する前に、 [[レポート] ページ](schedule-properties-reports-page.md) を使用して、どのレポートが共有スケジュールを現在使用しているかを確認します。</span><span class="sxs-lookup"><span data-stu-id="a4a26-108">Before deleting a shared schedule, use the [Reports page](schedule-properties-reports-page.md) to determine which reports are currently using the shared schedule.</span></span>  
  
 <span data-ttu-id="a4a26-109">ロール定義のうち削除できるのは、ロールの割り当てに現在使用されていないものだけです。</span><span class="sxs-lookup"><span data-stu-id="a4a26-109">For role definitions, you can only delete those that are not actively used in a role assignment.</span></span> <span data-ttu-id="a4a26-110">現在使用されているロールを削除しようとすると、レポート サーバーでロールが削除されずにエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a4a26-110">If you try to delete a role that is currently in use, the report server will not delete the role and you will see an error message to that effect.</span></span> <span data-ttu-id="a4a26-111">このページに含まれるロール定義が 1 つだけで、それが現在使用されていない場合、 **[OK]** をクリックするとその定義が削除されます。</span><span class="sxs-lookup"><span data-stu-id="a4a26-111">If this page contains a single role definition that is not currently in use, it will be deleted when you click **OK**.</span></span> <span data-ttu-id="a4a26-112">このページに複数のロールが含まれている場合、保持するロールと削除するロールを選択することはできません。</span><span class="sxs-lookup"><span data-stu-id="a4a26-112">If this page contains multiple roles, you cannot select which roles to keep or remove.</span></span> <span data-ttu-id="a4a26-113">**[OK]** をクリックすると、使用されていないロール定義がすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="a4a26-113">All unused role definitions will be deleted when you click **OK**.</span></span>  
  
 <span data-ttu-id="a4a26-114">削除操作は元に戻せません。</span><span class="sxs-lookup"><span data-stu-id="a4a26-114">You cannot undo a delete operation.</span></span> <span data-ttu-id="a4a26-115">削除したアイテムを復旧するには、そのアイテムを再作成するか、レポート サーバー データベースのバックアップ コピーを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4a26-115">If you want to recover an item that you deleted, you must either recreate it or restore a backup copy of the report server database.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a4a26-116">オプション</span><span class="sxs-lookup"><span data-stu-id="a4a26-116">Options</span></span>  
 <span data-ttu-id="a4a26-117">**Name**</span><span class="sxs-lookup"><span data-stu-id="a4a26-117">**Name**</span></span>  
 <span data-ttu-id="a4a26-118">削除するアイテムの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a4a26-118">Specifies the name of the item you are deleting.</span></span>  
  
 <span data-ttu-id="a4a26-119">**Type**</span><span class="sxs-lookup"><span data-stu-id="a4a26-119">**Type**</span></span>  
 <span data-ttu-id="a4a26-120">削除するアイテムの種類を表示します。</span><span class="sxs-lookup"><span data-stu-id="a4a26-120">Shows the type of item you are deleting.</span></span>  
  
 <span data-ttu-id="a4a26-121">**[所有者]**</span><span class="sxs-lookup"><span data-stu-id="a4a26-121">**Owner**</span></span>  
 <span data-ttu-id="a4a26-122">所有者の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="a4a26-122">Shows the name of the owner.</span></span> <span data-ttu-id="a4a26-123">ほとんどの場合は [システム] です。</span><span class="sxs-lookup"><span data-stu-id="a4a26-123">In most cases, this is System.</span></span>  
  
 <span data-ttu-id="a4a26-124">**状態**</span><span class="sxs-lookup"><span data-stu-id="a4a26-124">**Status**</span></span>  
 <span data-ttu-id="a4a26-125">削除操作の進行状況を表示します。</span><span class="sxs-lookup"><span data-stu-id="a4a26-125">Shows progress information for a delete operation.</span></span>  
  
 <span data-ttu-id="a4a26-126">**Error**</span><span class="sxs-lookup"><span data-stu-id="a4a26-126">**Error**</span></span>  
 <span data-ttu-id="a4a26-127">アイテムの削除中にエラーが発生した場合はエラー コードを表示します。</span><span class="sxs-lookup"><span data-stu-id="a4a26-127">Displays an error code if an error occurs while deleting an item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4a26-128">参照</span><span class="sxs-lookup"><span data-stu-id="a4a26-128">See Also</span></span>  
 <span data-ttu-id="a4a26-129">[アイテムの削除 &#40;Management Studio&#41;](delete-an-item-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="a4a26-129">[Delete an Item &#40;Management Studio&#41;](delete-an-item-management-studio.md) </span></span>  
 <span data-ttu-id="a4a26-130">[Management Studio のレポート サーバーの F1 ヘルプ](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="a4a26-130">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 [<span data-ttu-id="a4a26-131">スケジュールの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="a4a26-131">Create, Modify, and Delete Schedules</span></span>](../subscriptions/create-modify-and-delete-schedules.md)  
  
  

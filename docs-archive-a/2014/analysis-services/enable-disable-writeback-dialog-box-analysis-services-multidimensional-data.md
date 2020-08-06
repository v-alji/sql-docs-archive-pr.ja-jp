---
title: Enable-[書き戻しの無効化] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitiondesigner.writebackenabledisable.f1
ms.assetid: 2d254393-3f0d-4b70-8b98-87159f9f3639
author: minewiskan
ms.author: owend
ms.openlocfilehash: 54ee4597ee78f45682730bd0e8d7119d204eaf2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645890"
---
# <a name="enable-disable-writeback-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="3ece4-102">有効/[書き戻しの無効化] ダイアログボックス (Analysis Services-多次元データ)</span><span class="sxs-lookup"><span data-stu-id="3ece4-102">Enable-Disable Writeback Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="3ece4-103">**[書き戻しの有効化]/[書き戻しの無効化]** ダイアログ ボックスを使用すると、キューブ内のメジャー グループの書き戻しを有効または無効にできます。</span><span class="sxs-lookup"><span data-stu-id="3ece4-103">The **Enable/Disable Writeback** dialog box enables or disables writeback for a measure group in a cube.</span></span> <span data-ttu-id="3ece4-104">メジャー グループの書き戻しを有効にすると、書き戻しパーティションが定義され、そのメジャー グループの書き戻しテーブルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3ece4-104">Enabling writeback on a measure group defines a writeback partition and creates a writeback table for that measure group.</span></span> <span data-ttu-id="3ece4-105">メジャー グループの書き戻しを無効にすると、書き戻しパーティションが削除されます。ただし、予期しないデータの消失を避けるために、書き戻しテーブルは削除されません。</span><span class="sxs-lookup"><span data-stu-id="3ece4-105">Disabling writeback on a measure group removes the writeback partition but does not delete the writeback table, to avoid unanticipated data loss.</span></span> <span data-ttu-id="3ece4-106">**[書き戻しの有効化]/[書き戻しの無効化]** ダイアログ ボックスを表示するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="3ece4-106">The **Enable/Disable Writeback** dialog box is displayed by:</span></span>  
  
-   <span data-ttu-id="3ece4-107">キューブ デザイナーの **[パーティション]** タブの **[メジャー グループ]** ペインの **[書き戻しの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3ece4-107">Clicking **Writeback Settings** in the **Measure Groups** pane on the **Partitions** tab in Cube Designer.</span></span>  
  
-   <span data-ttu-id="3ece4-108">キューブ デザイナーの **[パーティション]** タブの **[メジャー グループ]** ペインの **[パーティション]** グリッドでパーティションを右クリックし、ショートカット メニューの **[書き戻しの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3ece4-108">Right-clicking a partition in the **Partitions** grid in the **Measure Groups** pane on the **Partitions** tab in Cube Designer and selecting **Writeback Settings** from the context menu.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3ece4-109">Options</span><span class="sxs-lookup"><span data-stu-id="3ece4-109">Options</span></span>  
 <span data-ttu-id="3ece4-110">**[テーブル名]**</span><span class="sxs-lookup"><span data-stu-id="3ece4-110">**Table name**</span></span>  
 <span data-ttu-id="3ece4-111">選択したパーティションに対して作成する書き戻しテーブルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="3ece4-111">Type the name of the writeback table to create for the selected partition.</span></span> <span data-ttu-id="3ece4-112">書き戻しテーブルには、クライアント アプリケーションからのメジャー グループへの変更が格納されます。</span><span class="sxs-lookup"><span data-stu-id="3ece4-112">The writeback table stores the changes made to the measure group from a client application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ece4-113">書き戻しが有効でない場合、このオプションは無効になります。</span><span class="sxs-lookup"><span data-stu-id="3ece4-113">This option is disabled if writeback is not enabled.</span></span>  
  
 <span data-ttu-id="3ece4-114">**データ ソース**</span><span class="sxs-lookup"><span data-stu-id="3ece4-114">**Data source**</span></span>  
 <span data-ttu-id="3ece4-115">書き戻しテーブルを格納するデータ ソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="3ece4-115">Select the data source to contain the writeback table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ece4-116">書き戻しが有効でない場合、このオプションは無効になります。</span><span class="sxs-lookup"><span data-stu-id="3ece4-116">This option is disabled if writeback is not enabled.</span></span>  
  
 <span data-ttu-id="3ece4-117">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="3ece4-117">**New**</span></span>  
 <span data-ttu-id="3ece4-118">クリックすると、 **[接続マネージャー]** ダイアログ ボックスが表示されます。このダイアログ ボックスで、書き戻しテーブルを格納する新しいデータ ソースを定義します。</span><span class="sxs-lookup"><span data-stu-id="3ece4-118">Click to display the **Connection Manager** dialog box and define a new data source to contain the writeback table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ece4-119">書き戻しが有効でない場合、このオプションは無効になります。</span><span class="sxs-lookup"><span data-stu-id="3ece4-119">This option is disabled if writeback is not enabled.</span></span>  
  
  

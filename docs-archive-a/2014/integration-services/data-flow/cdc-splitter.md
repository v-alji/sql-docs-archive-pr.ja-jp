---
title: CDC スプリッター | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsplitter.f1
ms.assetid: 167bc5c6-fa36-439d-987c-b20acd1a77e2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 45dd16602625b28d2ca7e16f2fa6b0d62294fe81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642208"
---
# <a name="cdc-splitter"></a><span data-ttu-id="a5c70-102">CDC スプリッター</span><span class="sxs-lookup"><span data-stu-id="a5c70-102">CDC Splitter</span></span>
  <span data-ttu-id="a5c70-103">CDC スプリッターは、CDC ソース データの変更行の単一フローを、挿入、更新、削除の各操作のための個別のデータ フローに分割します。</span><span class="sxs-lookup"><span data-stu-id="a5c70-103">The CDC splitter splits a single flow of change rows from a CDC source data flow into different data flows for Insert, Update and Delete operations.</span></span> <span data-ttu-id="a5c70-104">データベースは、必須の列 `__$operation` と、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 変更テーブル内のその標準の値に基づいて分割されます。</span><span class="sxs-lookup"><span data-stu-id="a5c70-104">The data flow is split based on the required column `__$operation` and its standard values in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] change tables.</span></span>  
  
|<span data-ttu-id="a5c70-105">操作の値</span><span class="sxs-lookup"><span data-stu-id="a5c70-105">Value of Operation</span></span>|<span data-ttu-id="a5c70-106">Output</span><span class="sxs-lookup"><span data-stu-id="a5c70-106">Output</span></span>|<span data-ttu-id="a5c70-107">説明</span><span class="sxs-lookup"><span data-stu-id="a5c70-107">Description</span></span>|  
|------------------------|------------|-----------------|  
|<span data-ttu-id="a5c70-108">1</span><span class="sxs-lookup"><span data-stu-id="a5c70-108">1</span></span>|<span data-ttu-id="a5c70-109">削除</span><span class="sxs-lookup"><span data-stu-id="a5c70-109">Delete</span></span>|<span data-ttu-id="a5c70-110">削除された行</span><span class="sxs-lookup"><span data-stu-id="a5c70-110">Deleted Row</span></span>|  
|<span data-ttu-id="a5c70-111">2</span><span class="sxs-lookup"><span data-stu-id="a5c70-111">2</span></span>|<span data-ttu-id="a5c70-112">挿入</span><span class="sxs-lookup"><span data-stu-id="a5c70-112">Insert</span></span>|<span data-ttu-id="a5c70-113">挿入された行 ( **"結合を含む差分"** CDC モードを使用する場合は使用不可)</span><span class="sxs-lookup"><span data-stu-id="a5c70-113">Inserted row (not available when using **Net with Merge** CDC mode)</span></span>|  
|<span data-ttu-id="a5c70-114">3</span><span class="sxs-lookup"><span data-stu-id="a5c70-114">3</span></span>|<span data-ttu-id="a5c70-115">更新</span><span class="sxs-lookup"><span data-stu-id="a5c70-115">Update</span></span>|<span data-ttu-id="a5c70-116">更新前の行 ( **"古い値を含むすべて"** CDC モードの場合のみ使用可)</span><span class="sxs-lookup"><span data-stu-id="a5c70-116">Before-update row (available only when using **All with Old Values** CDC mode)</span></span>|  
|<span data-ttu-id="a5c70-117">4</span><span class="sxs-lookup"><span data-stu-id="a5c70-117">4</span></span>|<span data-ttu-id="a5c70-118">更新</span><span class="sxs-lookup"><span data-stu-id="a5c70-118">Update</span></span>|<span data-ttu-id="a5c70-119">更新後の行 (更新前と同じ)</span><span class="sxs-lookup"><span data-stu-id="a5c70-119">After-update row (follows the Before-update)</span></span>|  
|<span data-ttu-id="a5c70-120">5</span><span class="sxs-lookup"><span data-stu-id="a5c70-120">5</span></span>|<span data-ttu-id="a5c70-121">更新</span><span class="sxs-lookup"><span data-stu-id="a5c70-121">Update</span></span>|<span data-ttu-id="a5c70-122">マージ行 ( **"結合を含む差分"** CDC モードを使用する場合のみ使用可)</span><span class="sxs-lookup"><span data-stu-id="a5c70-122">Merge row (available only when using **Net with Merge** CDC mode)</span></span>|  
|<span data-ttu-id="a5c70-123">その他</span><span class="sxs-lookup"><span data-stu-id="a5c70-123">Other</span></span>|<span data-ttu-id="a5c70-124">エラー</span><span class="sxs-lookup"><span data-stu-id="a5c70-124">Error</span></span>||  
  
 <span data-ttu-id="a5c70-125">スプリッターを使用して、定義済みの挿入、削除、更新の各出力に接続し、さらに処理を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="a5c70-125">You can use the splitter to connect to pre-defined INSERT, DELETE, and UPDATE outputs for further processing.</span></span>  
  
 <span data-ttu-id="a5c70-126">CDC スプリッター変換には、1 つの標準入力と 1 つのエラー出力があります。</span><span class="sxs-lookup"><span data-stu-id="a5c70-126">The CDC Splitter transformation has one regular input and one error output.</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="a5c70-127">エラー処理</span><span class="sxs-lookup"><span data-stu-id="a5c70-127">Error Handling</span></span>  
 <span data-ttu-id="a5c70-128">CDC スプリッター変換にはエラー出力があります。</span><span class="sxs-lookup"><span data-stu-id="a5c70-128">The CDC Splitter transformation has an error output.</span></span> <span data-ttu-id="a5c70-129">$operation 列の値が無効な入力行はエラーと見なされ、入力の **ErrorRowDisposition** プロパティに従って処理されます。</span><span class="sxs-lookup"><span data-stu-id="a5c70-129">Input rows with an invalid value of the $operation column are considered erroneous and are handled according to the **ErrorRowDisposition** property of the input.</span></span>  
  
 <span data-ttu-id="a5c70-130">コンポーネントのエラー出力には、次の出力列があります。</span><span class="sxs-lookup"><span data-stu-id="a5c70-130">The component error output includes the following output columns:</span></span>  
  
-   <span data-ttu-id="a5c70-131">**エラー コード**: 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="a5c70-131">**Error Code**: Set to 1.</span></span>  
  
-   <span data-ttu-id="a5c70-132">**エラー列**: (変換エラーの) エラーの原因となるソース列。</span><span class="sxs-lookup"><span data-stu-id="a5c70-132">**Error Column**: The source column causing the error (for conversion errors).</span></span>  
  
-   <span data-ttu-id="a5c70-133">**エラー行の列**: エラーの原因となった行の入力列。</span><span class="sxs-lookup"><span data-stu-id="a5c70-133">**Error Row Columns**: The input columns of the row that caused the error.</span></span>  
  
## <a name="configuring-the-cdc-splitter"></a><span data-ttu-id="a5c70-134">CDC スプリッターの構成</span><span class="sxs-lookup"><span data-stu-id="a5c70-134">Configuring the CDC Splitter</span></span>  
 <span data-ttu-id="a5c70-135">CDC スプリッターに構成可能なプロパティはありません。</span><span class="sxs-lookup"><span data-stu-id="a5c70-135">There are no configurable properties for the CDC splitter.</span></span>  
  
 <span data-ttu-id="a5c70-136">CDC スプリッターの使用方法の詳細については、「Microsoft SQL Server Integration Services の CDC コンポーネント」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5c70-136">For more information about using the CDC splitter, see CDC Components for Microsoft SQL Server Integration Services.</span></span>  
  
 <span data-ttu-id="a5c70-137">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a5c70-137">The **Advanced Editor** dialog box contains the properties that can be set programmatically.</span></span>  
  
 <span data-ttu-id="a5c70-138">**[詳細エディター]** ダイアログ ボックスを開くには、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="a5c70-138">To open the **Advanced Editor** dialog box:</span></span>  
  
-   <span data-ttu-id="a5c70-139">**プロジェクトの** [データ フロー] [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 画面で、CDC スプリッターを右クリックし、 **[詳細エディターの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5c70-139">In the **Data Flow** screen of your [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project, right click the CDC splitter and select **Show Advanced Editor**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5c70-140">参照</span><span class="sxs-lookup"><span data-stu-id="a5c70-140">See Also</span></span>  
 [<span data-ttu-id="a5c70-141">変更の種類に応じた CDC ストリームのダイレクト</span><span class="sxs-lookup"><span data-stu-id="a5c70-141">Direct the CDC Stream According to the Type of Change</span></span>](direct-the-cdc-stream-according-to-the-type-of-change.md)  
  
  

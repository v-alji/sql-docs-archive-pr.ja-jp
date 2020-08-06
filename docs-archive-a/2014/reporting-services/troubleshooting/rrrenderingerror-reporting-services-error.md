---
title: rrRenderingError - Reporting Services エラー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rrRenderingError
ms.assetid: 0751efc3-b81b-44ee-8aac-8560f86ca322
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b44b042c5f3c0cfdb9ffb99d3f45ed073beb972a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715981"
---
# <a name="rrrenderingerror---reporting-services-error"></a><span data-ttu-id="7e06c-102">rrRenderingError - Reporting Services エラー</span><span class="sxs-lookup"><span data-stu-id="7e06c-102">rrRenderingError - Reporting Services Error</span></span>
    
## <a name="details"></a><span data-ttu-id="7e06c-103">詳細</span><span class="sxs-lookup"><span data-stu-id="7e06c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7e06c-104">製品名</span><span class="sxs-lookup"><span data-stu-id="7e06c-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="7e06c-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="7e06c-105">Event ID</span></span>|<span data-ttu-id="7e06c-106">rrRenderingError</span><span class="sxs-lookup"><span data-stu-id="7e06c-106">rrRenderingError</span></span>|  
|<span data-ttu-id="7e06c-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="7e06c-107">Event Source</span></span>|<span data-ttu-id="7e06c-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings.resources.Strings</span><span class="sxs-lookup"><span data-stu-id="7e06c-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings.resources.Strings</span></span>|  
|<span data-ttu-id="7e06c-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="7e06c-109">Component</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="7e06c-110">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="7e06c-110">Message Text</span></span>|<span data-ttu-id="7e06c-111">レポートの表示中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="7e06c-111">An error occurred during rendering of the report.</span></span> <span data-ttu-id="7e06c-112">(rrRenderingError) %1</span><span class="sxs-lookup"><span data-stu-id="7e06c-112">(rrRenderingError) %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7e06c-113">説明</span><span class="sxs-lookup"><span data-stu-id="7e06c-113">Explanation</span></span>  
 <span data-ttu-id="7e06c-114">このメッセージは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] がレポートを表示またはエクスポートできない場合に返されます。</span><span class="sxs-lookup"><span data-stu-id="7e06c-114">This message is returned when [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] cannot render or export the report.</span></span>  
  
 <span data-ttu-id="7e06c-115">サイズがサポートされていないという内容のメッセージである場合、一般的な原因として、指定された RDL ページ サイズが無効であることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="7e06c-115">A message that indicates that the size is not supported is typically caused when the specified RDL page size is not valid.</span></span> <span data-ttu-id="7e06c-116">有効な RDL ページ サイズを指定してから再試行してください。</span><span class="sxs-lookup"><span data-stu-id="7e06c-116">Specify a valid RDL page size and then try again.</span></span>  
  
 <span data-ttu-id="7e06c-117">RDL サイズの単位がサポートされていないという内容のメッセージである場合、一般的な原因として、サポートされていない種類の単位が指定されたことが考えられます。</span><span class="sxs-lookup"><span data-stu-id="7e06c-117">A message that indicates that an RDL size measurement is not supported is typically caused when an unsupported unit type is specified.</span></span> <span data-ttu-id="7e06c-118">有効な単位は、cm、in、mm、pc、および pt です。</span><span class="sxs-lookup"><span data-stu-id="7e06c-118">Valid unit types are cm, in, mm, pc, and pt.</span></span> <span data-ttu-id="7e06c-119">有効な単位を指定してから再試行してください。</span><span class="sxs-lookup"><span data-stu-id="7e06c-119">Specify a valid unit type and then try again.</span></span>  
  
 <span data-ttu-id="7e06c-120">負のサイズはサポートされていないという内容のメッセージである場合、一般的な原因として、ページ サイズに負の値 (-5 cm など) が指定されたことが考えられます。</span><span class="sxs-lookup"><span data-stu-id="7e06c-120">A message that indicates that a negative size is not supported is typically caused when a negative measurement for the page size, for example -5 cm, is specified.</span></span> <span data-ttu-id="7e06c-121">ページ サイズに正の値を指定してから再試行してください。</span><span class="sxs-lookup"><span data-stu-id="7e06c-121">Specify a positive number for the page size and then try again.</span></span>  
  
 <span data-ttu-id="7e06c-122">RDL サイズの指定が範囲外であるという内容のメッセージである場合、一般的な原因として、ページ サイズに指定された値が、有効なページ余白サイズの範囲を超えていることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="7e06c-122">A message that indicates that an RDL size is specified out of range is typically caused when a measurement for the page size is outside of the valid page margin size.</span></span> <span data-ttu-id="7e06c-123">ページ余白サイズの範囲に収まる有効な値を指定してください。</span><span class="sxs-lookup"><span data-stu-id="7e06c-123">Specify a measurement for the page size that is within the valid page margin sizes.</span></span>  
  
 <span data-ttu-id="7e06c-124">指定された色がサポートされていないという内容のメッセージである場合、一般的な原因として、RDL で指定された色が無効であることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="7e06c-124">A message that indicates that a color specified is not supported is typically caused when a color specified in the RDL is not valid.</span></span> <span data-ttu-id="7e06c-125">RDL でサポートされている色を選択してから再試行してください。</span><span class="sxs-lookup"><span data-stu-id="7e06c-125">Choose a color supported by RDL and then try again.</span></span>  
  
 <span data-ttu-id="7e06c-126">アクション ラベルは 1 つのアクションを使用している場合にのみ省略でき、複数のアクションを追加する場合はアクションごとにラベルが必要であるという内容のメッセージである場合、一般的な原因として、指定されたアクション ラベルが無効であることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="7e06c-126">A message that indicates that the action label is only optional when using a single action and that adding multiple actions requires labels for each action is typically caused when an action label is specified and it is not valid.</span></span> <span data-ttu-id="7e06c-127">アクションごとに有効なアクション ラベルを指定してください。</span><span class="sxs-lookup"><span data-stu-id="7e06c-127">Specify a valid action label for each action.</span></span>  
  
 <span data-ttu-id="7e06c-128">スタイル引数を特定の型にする必要があるという内容のメッセージである場合、一般的な原因として、そのデータ型に対して誤ったスタイル値が指定されていることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="7e06c-128">A message that indicates the style argument has to be of a specific type is typically caused when an incorrect style value for the data type is specified.</span></span> <span data-ttu-id="7e06c-129">RDL 仕様では、各種の RDL 要素のスタイル値に使用できる有効な型が規定されています。</span><span class="sxs-lookup"><span data-stu-id="7e06c-129">The RDL specification identifies the valid types that you can use in the style values of different RDL elements.</span></span> <span data-ttu-id="7e06c-130">たとえば、背景色のスタイル値に "2pt" を指定したり、高さに "true" を指定したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="7e06c-130">For example, an incorrect style value for background color is "2pt" and incorrect value for height is "true".</span></span> <span data-ttu-id="7e06c-131">正しい値を指定してから再試行してください。</span><span class="sxs-lookup"><span data-stu-id="7e06c-131">Specify a correct value and then try again.</span></span>  
  
 <span data-ttu-id="7e06c-132">罫線のスタイルがサポートされていないという内容のメッセージである場合、一般的な原因として、指定された罫線のスタイルが無効であることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="7e06c-132">A message that indicates that the border style is not supported is typically caused when the border style specified is not valid.</span></span> <span data-ttu-id="7e06c-133">サポートされている罫線のスタイルを指定してから再試行してください。</span><span class="sxs-lookup"><span data-stu-id="7e06c-133">Specify a supported border style and then try again.</span></span>  
  
 <span data-ttu-id="7e06c-134">画像の MIME の種類がサポートされていないという内容のメッセージである場合、一般的な原因として、画像レポート アイテムに指定された MIME の種類が無効であることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="7e06c-134">A message that indicates that the image mimetype is not supported is typically caused when the specified mimetype for an image report item is not valid.</span></span> <span data-ttu-id="7e06c-135">そのレポート アイテムにサポートされている MIME の種類を指定してから再試行してください。</span><span class="sxs-lookup"><span data-stu-id="7e06c-135">Specify a supported mimetype for the report item and then try again.</span></span>  
  
 <span data-ttu-id="7e06c-136">行数が 1 シートの上限値を超えたという内容のメッセージである場合、一般的な原因として、Excel ワークシートの行数が上限を超えたことが考えられます。</span><span class="sxs-lookup"><span data-stu-id="7e06c-136">A message that indicates that the number of rows exceeds the maximum possible rows per sheet is typically caused when the number of rows in an Excel worksheet is exceeded.</span></span> <span data-ttu-id="7e06c-137">Excel でサポートされる最大行数は 65,000 行です。</span><span class="sxs-lookup"><span data-stu-id="7e06c-137">Excel supports up to 65,000 rows.</span></span>  
  
 <span data-ttu-id="7e06c-138">列数が 1 シートの上限値を超えたという内容のメッセージである場合、一般的な原因として、Excel ワークシートの列数が上限を超えたことが考えられます。</span><span class="sxs-lookup"><span data-stu-id="7e06c-138">A message that indicates that the number of columns exceeds the maximum possible columns per sheet is typically caused when the number of columns in an Excel worksheet is exceeded.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7e06c-139">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="7e06c-139">User Action</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="7e06c-140">内部使用のみ</span><span class="sxs-lookup"><span data-stu-id="7e06c-140">Internal-Only</span></span>  
  

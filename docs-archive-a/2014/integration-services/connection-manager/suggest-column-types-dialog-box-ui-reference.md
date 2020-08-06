---
title: '[列の型の推測] ダイアログ ボックスの UI リファレンス | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.suggestdatatypes.f1
ms.assetid: 8d5652e0-cf57-483f-828b-10f00c08418b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4cbca2a3186a58b1148eb9627825fdfddf334339
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741181"
---
# <a name="suggest-column-types-dialog-box-ui-reference"></a><span data-ttu-id="4f277-102">[列の型の推測] ダイアログ ボックスの UI リファレンス</span><span class="sxs-lookup"><span data-stu-id="4f277-102">Suggest Column Types Dialog Box UI Reference</span></span>
  <span data-ttu-id="4f277-103">**[列の型の推測]** ダイアログ ボックスを使用すると、フラット ファイル接続マネージャー内の列のデータ型および長さを、ファイルの内容のサンプリングに基づいて識別できます。</span><span class="sxs-lookup"><span data-stu-id="4f277-103">Use the **Suggest Column Types** dialog box to identify the data type and length of columns in a Flat File Connection Manager based on a sampling of the file content.</span></span>  
  
 <span data-ttu-id="4f277-104">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]で使用されるデータ型の詳細については、「 [Integration Services のデータ型](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f277-104">To learn more about the data types used by [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="4f277-105">オプション</span><span class="sxs-lookup"><span data-stu-id="4f277-105">Options</span></span>  
 <span data-ttu-id="4f277-106">**[行数]**</span><span class="sxs-lookup"><span data-stu-id="4f277-106">**Number of rows**</span></span>  
 <span data-ttu-id="4f277-107">アルゴリズムで使用するサンプル内の行数を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="4f277-107">Type or select the number of rows in the sample that the algorithm uses.</span></span>  
  
 <span data-ttu-id="4f277-108">**[最小の整数データ型を推測する]**</span><span class="sxs-lookup"><span data-stu-id="4f277-108">**Suggest the smallest integer data type**</span></span>  
 <span data-ttu-id="4f277-109">評価をスキップする場合は、このチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="4f277-109">Clear this check box to skip the assessment.</span></span> <span data-ttu-id="4f277-110">オンにすると、整数の数値データを含む列で使用できる最小の整数データ型が決定されます。</span><span class="sxs-lookup"><span data-stu-id="4f277-110">If selected, determines the smallest possible integer data type for columns that contain integral numeric data.</span></span>  
  
 <span data-ttu-id="4f277-111">**[最小の実数データ型を推測する]**</span><span class="sxs-lookup"><span data-stu-id="4f277-111">**Suggest the smallest real data type**</span></span>  
 <span data-ttu-id="4f277-112">評価をスキップする場合は、このチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="4f277-112">Clear this check box to skip the assessment.</span></span> <span data-ttu-id="4f277-113">オンにすると、実数データを含む列で、より小さい実数データ型 DT_R4 を使用できるかどうかが決定されます。</span><span class="sxs-lookup"><span data-stu-id="4f277-113">If selected, determines whether columns that contain real numeric data can use the smaller real data type, DT_R4.</span></span>  
  
 <span data-ttu-id="4f277-114">**[以下の値を使用してブール型の列を特定する]**</span><span class="sxs-lookup"><span data-stu-id="4f277-114">**Identify Boolean columns using the following values**</span></span>  
 <span data-ttu-id="4f277-115">ブール値 True および False として使用する 2 つの値を入力します。</span><span class="sxs-lookup"><span data-stu-id="4f277-115">Type the two values that you want to use as the Boolean values true and false.</span></span> <span data-ttu-id="4f277-116">値はコンマで区切る必要があり、最初の値が True を表すようにします。</span><span class="sxs-lookup"><span data-stu-id="4f277-116">The values must be separated by a comma, and the first value represents True.</span></span>  
  
 <span data-ttu-id="4f277-117">**[文字列型の列を埋め込む]**</span><span class="sxs-lookup"><span data-stu-id="4f277-117">**Pad string columns**</span></span>  
 <span data-ttu-id="4f277-118">このチェック ボックスをオンにすると、文字列の埋め込みが有効になります。</span><span class="sxs-lookup"><span data-stu-id="4f277-118">Select this check box to enable string padding.</span></span>  
  
 <span data-ttu-id="4f277-119">**[埋め込み率]**</span><span class="sxs-lookup"><span data-stu-id="4f277-119">**Percent padding**</span></span>  
 <span data-ttu-id="4f277-120">文字データ型の列の長さを増やすために使用する、列の長さに対する割合を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="4f277-120">Type or select the percentage of the column lengths by which to increase the length of columns for character data types.</span></span> <span data-ttu-id="4f277-121">割合は整数にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f277-121">The percentage must be an integer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f277-122">参照</span><span class="sxs-lookup"><span data-stu-id="4f277-122">See Also</span></span>  
 <span data-ttu-id="4f277-123">[Integration Services のエラーおよびメッセージのリファレンス](../integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="4f277-123">[Integration Services Error and Message Reference](../integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="4f277-124">フラット ファイル接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="4f277-124">Flat File Connection Manager</span></span>](file-connection-manager.md)  
  
  

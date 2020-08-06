---
title: '[行サンプリング変換エディター] ([サンプリング] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.ROWSAMPLINGTRANSFORMATION.COLUMNS.F1
- sql12.dts.designer.rowsamplingtransformation.f1
helpviewer_keywords:
- Row Sampling Transformation Editor
ms.assetid: 544c7709-6de0-4c08-bda3-759985be9a05
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 26d0c0439e548172225f02220d8f6814a1168ea9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713261"
---
# <a name="row-sampling-transformation-editor-sampling-page"></a><span data-ttu-id="cabb6-102">行サンプリング変換エディター ([サンプリング] ページ)</span><span class="sxs-lookup"><span data-stu-id="cabb6-102">Row Sampling Transformation Editor (Sampling Page)</span></span>
  <span data-ttu-id="cabb6-103">**[行サンプリング変換エディター]** ダイアログ ボックスを使用すると、指定された行数を使用して、入力の一部をサンプルに分割できます。</span><span class="sxs-lookup"><span data-stu-id="cabb6-103">Use the **Row Sampling Transformation Editor** dialog box to split a portion of an input into a sample using a specified number of rows.</span></span> <span data-ttu-id="cabb6-104">この変換は、入力を 2 つの別個の出力に分割します。</span><span class="sxs-lookup"><span data-stu-id="cabb6-104">This transformation divides the input into two separate outputs.</span></span>  
  
 <span data-ttu-id="cabb6-105">行サンプリング変換の詳細については、「 [Row Sampling Transformation](data-flow/transformations/row-sampling-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cabb6-105">To learn more about the Row Sampling transformation, see [Row Sampling Transformation](data-flow/transformations/row-sampling-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="cabb6-106">Options</span><span class="sxs-lookup"><span data-stu-id="cabb6-106">Options</span></span>  
 <span data-ttu-id="cabb6-107">**行数**</span><span class="sxs-lookup"><span data-stu-id="cabb6-107">**Number of rows**</span></span>  
 <span data-ttu-id="cabb6-108">サンプルとして使用する入力における行数を指定します。</span><span class="sxs-lookup"><span data-stu-id="cabb6-108">Specify the number of rows from the input to use as a sample.</span></span>  
  
 <span data-ttu-id="cabb6-109">このプロパティの値は、プロパティ式を使用して指定することができます。</span><span class="sxs-lookup"><span data-stu-id="cabb6-109">The value of this property can be specified by using a property expression.</span></span>  
  
 <span data-ttu-id="cabb6-110">**[サンプル出力名]**</span><span class="sxs-lookup"><span data-stu-id="cabb6-110">**Sample output name**</span></span>  
 <span data-ttu-id="cabb6-111">サンプリングされた行を含める出力の一意な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="cabb6-111">Provide a unique name for the output that will include the sampled rows.</span></span> <span data-ttu-id="cabb6-112">指定した名前は、SSIS デザイナー内に表示されます。</span><span class="sxs-lookup"><span data-stu-id="cabb6-112">The name provided will be displayed within SSIS Designer.</span></span>  
  
 <span data-ttu-id="cabb6-113">**[選択されていない出力名]**</span><span class="sxs-lookup"><span data-stu-id="cabb6-113">**Unselected output name**</span></span>  
 <span data-ttu-id="cabb6-114">サンプリングから除外された行を含む出力の一意な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="cabb6-114">Provide a unique name for the output that will contain the rows excluded from the sampling.</span></span> <span data-ttu-id="cabb6-115">指定した名前は、SSIS デザイナー内に表示されます。</span><span class="sxs-lookup"><span data-stu-id="cabb6-115">The name provided will be displayed within SSIS Designer.</span></span>  
  
 <span data-ttu-id="cabb6-116">**[次のランダム シードを使用する]**</span><span class="sxs-lookup"><span data-stu-id="cabb6-116">**Use the following random seed**</span></span>  
 <span data-ttu-id="cabb6-117">変換でサンプルを作成するために使用する乱数ジェネレーターのサンプリング シードを指定します。</span><span class="sxs-lookup"><span data-stu-id="cabb6-117">Specify the sampling seed for the random number generator that the transformation uses to create a sample.</span></span> <span data-ttu-id="cabb6-118">このオプションは、開発およびテスト用にのみ使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cabb6-118">This is only recommended for development and testing.</span></span> <span data-ttu-id="cabb6-119">ランダム シードを指定しなかった場合は、Microsoft Windows のティック数がシードとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="cabb6-119">The transformation uses the Microsoft Windows tick count as a seed if a random seed is not specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cabb6-120">参照</span><span class="sxs-lookup"><span data-stu-id="cabb6-120">See Also</span></span>  
 <span data-ttu-id="cabb6-121">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="cabb6-121">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="cabb6-122">比率サンプリング変換</span><span class="sxs-lookup"><span data-stu-id="cabb6-122">Percentage Sampling Transformation</span></span>](data-flow/transformations/percentage-sampling-transformation.md)  
  
  

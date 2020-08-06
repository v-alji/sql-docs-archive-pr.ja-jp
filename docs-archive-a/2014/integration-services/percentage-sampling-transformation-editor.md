---
title: 比率サンプリング変換エディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.percentagesamplingtransformation.f1
helpviewer_keywords:
- Percentage Sampling Transformation Editor
ms.assetid: 2c40d804-26a3-4d35-809b-bc923d83d451
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c4dbd96ab952b6c88bdaa7bf56a0a2f1b3585c57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632550"
---
# <a name="percentage-sampling-transformation-editor"></a><span data-ttu-id="52b01-102">比率サンプリング変換エディター</span><span class="sxs-lookup"><span data-stu-id="52b01-102">Percentage Sampling Transformation Editor</span></span>
  <span data-ttu-id="52b01-103">**[比率サンプリング変換エディター]** ダイアログ ボックスを使用すると、指定された行の割合を使用して、入力の一部をサンプルに分割できます。</span><span class="sxs-lookup"><span data-stu-id="52b01-103">Use the **Percentage Sampling Transformation Editor** dialog box to split part of an input into a sample using a specified percentage of rows.</span></span> <span data-ttu-id="52b01-104">この変換は、入力を 2 つの別個の出力に分割します。</span><span class="sxs-lookup"><span data-stu-id="52b01-104">This transformation divides the input into two separate outputs.</span></span>  
  
 <span data-ttu-id="52b01-105">比率サンプリング変換の詳細については、「 [Percentage Sampling Transformation](data-flow/transformations/percentage-sampling-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52b01-105">To learn more about the percentage sampling transformation, see [Percentage Sampling Transformation](data-flow/transformations/percentage-sampling-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="52b01-106">Options</span><span class="sxs-lookup"><span data-stu-id="52b01-106">Options</span></span>  
 <span data-ttu-id="52b01-107">**[行の割合]**</span><span class="sxs-lookup"><span data-stu-id="52b01-107">**Percentage of rows**</span></span>  
 <span data-ttu-id="52b01-108">サンプルとして使用する入力における行の割合を指定します。</span><span class="sxs-lookup"><span data-stu-id="52b01-108">Specify the percentage of rows in the input to use as a sample.</span></span>  
  
 <span data-ttu-id="52b01-109">このプロパティの値は、プロパティ式を使用して指定することができます。</span><span class="sxs-lookup"><span data-stu-id="52b01-109">The value of this property can be specified by using a property expression.</span></span>  
  
 <span data-ttu-id="52b01-110">**[サンプル出力名]**</span><span class="sxs-lookup"><span data-stu-id="52b01-110">**Sample output name**</span></span>  
 <span data-ttu-id="52b01-111">サンプリングされた行を含める出力の一意な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="52b01-111">Provide a unique name for the output that will include the sampled rows.</span></span> <span data-ttu-id="52b01-112">指定された名前は、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="52b01-112">The name provided will be displayed within the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="52b01-113">**[選択されていない出力名]**</span><span class="sxs-lookup"><span data-stu-id="52b01-113">**Unselected output name**</span></span>  
 <span data-ttu-id="52b01-114">サンプリングから除外された行を含む出力の一意な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="52b01-114">Provide a unique name for the output that will contain the rows excluded from the sampling.</span></span> <span data-ttu-id="52b01-115">指定された名前は、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="52b01-115">The name provided will be displayed within the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="52b01-116">**[次のランダム シードを使用する]**</span><span class="sxs-lookup"><span data-stu-id="52b01-116">**Use the following random seed**</span></span>  
 <span data-ttu-id="52b01-117">変換でサンプルを作成するために使用する乱数ジェネレーターのサンプリング シードを指定します。</span><span class="sxs-lookup"><span data-stu-id="52b01-117">Specify the sampling seed for the random number generator that the transformation uses to create a sample.</span></span> <span data-ttu-id="52b01-118">このオプションは、開発およびテスト用にのみ使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="52b01-118">This is only recommended for development and testing.</span></span> <span data-ttu-id="52b01-119">ランダム シードが指定されない場合は、Microsoft Windows のティック数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="52b01-119">The transformation uses the Microsoft Windows tick count if a random seed is not specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52b01-120">参照</span><span class="sxs-lookup"><span data-stu-id="52b01-120">See Also</span></span>  
 <span data-ttu-id="52b01-121">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="52b01-121">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="52b01-122">行サンプリング変換</span><span class="sxs-lookup"><span data-stu-id="52b01-122">Row Sampling Transformation</span></span>](data-flow/transformations/row-sampling-transformation.md)  
  
  
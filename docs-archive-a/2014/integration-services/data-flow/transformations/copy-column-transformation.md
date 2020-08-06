---
title: 列コピー変換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.copycolumntrans.f1
helpviewer_keywords:
- columns [Integration Services], copying
- copying columns
- Copy Column transformation
ms.assetid: 1c72a313-9026-46bc-a57f-c6b3f47346f8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fd2745070a92ab71e89f3bfa9edd8673b676632b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642201"
---
# <a name="copy-column-transformation"></a><span data-ttu-id="7c7d5-102">列コピー変換</span><span class="sxs-lookup"><span data-stu-id="7c7d5-102">Copy Column Transformation</span></span>
  <span data-ttu-id="7c7d5-103">列コピー変換は、入力列をコピーして新しい列を変換出力に追加し、新しい列を作成します。</span><span class="sxs-lookup"><span data-stu-id="7c7d5-103">The Copy Column transformation creates new columns by copying input columns and adding the new columns to the transformation output.</span></span> <span data-ttu-id="7c7d5-104">後のデータ フローで、その列コピーに別の変換を適用できます。</span><span class="sxs-lookup"><span data-stu-id="7c7d5-104">Later in the data flow, different transformations can be applied to the column copies.</span></span> <span data-ttu-id="7c7d5-105">たとえば、列コピー変換を使用して列のコピーを作成した後、文字マップ変換を使用してそのコピーしたデータを大文字に変換したり、集計変換を使用して新しい列に集計を適用したりできます。</span><span class="sxs-lookup"><span data-stu-id="7c7d5-105">For example, you can use the Copy Column transformation to create a copy of a column and then convert the copied data to uppercase characters by using the Character Map transformation, or apply aggregations to the new column by using the Aggregate transformation.</span></span>  
  
## <a name="configuration-of-the-copy-column-transformation"></a><span data-ttu-id="7c7d5-106">列コピー変換の構成</span><span class="sxs-lookup"><span data-stu-id="7c7d5-106">Configuration of the Copy Column Transformation</span></span>  
 <span data-ttu-id="7c7d5-107">列コピー変換を構成するには、コピーする入力列を指定します。</span><span class="sxs-lookup"><span data-stu-id="7c7d5-107">You configure the Copy Column transformation by specifying the input columns to copy.</span></span> <span data-ttu-id="7c7d5-108">一度の操作で、1 列の複数コピー、または複数列の複数コピーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="7c7d5-108">You can create multiple copies of a column, or create copies of multiple columns in one operation.</span></span>  
  
 <span data-ttu-id="7c7d5-109">この変換は 1 つの入力と 1 つの出力をとります。</span><span class="sxs-lookup"><span data-stu-id="7c7d5-109">This transformation has one input and one output.</span></span> <span data-ttu-id="7c7d5-110">エラー出力はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="7c7d5-110">It does not support an error output.</span></span>  
  
 <span data-ttu-id="7c7d5-111">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="7c7d5-111">You can set properties through the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="7c7d5-112">**[列コピー変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、「 [列コピー変換エディター](../../copy-column-transformation-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7c7d5-112">For more information about the properties that you can set in the **Copy Column Transformation Editor** dialog box, see [Copy Column Transformation Editor](../../copy-column-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="7c7d5-113">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="7c7d5-113">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="7c7d5-114">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7c7d5-114">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="7c7d5-115">Common Properties</span><span class="sxs-lookup"><span data-stu-id="7c7d5-115">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="7c7d5-116">変換のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="7c7d5-116">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="7c7d5-117">プロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](../set-the-properties-of-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7c7d5-117">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c7d5-118">参照</span><span class="sxs-lookup"><span data-stu-id="7c7d5-118">See Also</span></span>  
 <span data-ttu-id="7c7d5-119">[データ フロー](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="7c7d5-119">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="7c7d5-120">Integration Services の変換</span><span class="sxs-lookup"><span data-stu-id="7c7d5-120">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  

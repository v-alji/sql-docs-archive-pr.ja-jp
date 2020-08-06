---
title: 行数変換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rowcounttrans.f1
helpviewer_keywords:
- updating variables
- Row Count transformation
- number of rows
- variables [Integration Services], updating
- counting rows
ms.assetid: b68293b9-a68c-40be-9d81-77342da1be29
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1b0940d608aeaa96b7ec43fa4486944ce0f887e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743413"
---
# <a name="row-count-transformation"></a><span data-ttu-id="59ad3-102">行数変換</span><span class="sxs-lookup"><span data-stu-id="59ad3-102">Row Count Transformation</span></span>
  <span data-ttu-id="59ad3-103">行数変換は、行がデータ フローを通過するときに行をカウントし、最終的な行数を変数に格納します。</span><span class="sxs-lookup"><span data-stu-id="59ad3-103">The Row Count transformation counts rows as they pass through a data flow and stores the final count in a variable.</span></span>  
  
 <span data-ttu-id="59ad3-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] パッケージで行数を使用して、スクリプト、式、およびプロパティ式で使用される変数を更新できます。</span><span class="sxs-lookup"><span data-stu-id="59ad3-104">A [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] package can use row counts to update the variables used in scripts, expressions, and property expressions.</span></span> <span data-ttu-id="59ad3-105">(たとえば、行数を格納する変数を使用して、電子メールのメッセージ テキストを更新して行数を含めることができます)。行数変換で使用する変数は、既存の変数で、行数変換を使用するデータ フローが属するデータ フロー タスクの範囲に含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="59ad3-105">(For example, the variable that stores the row count can update the message text in an e-mail message to include the number of rows.) The variable that the Row Count transformation uses must already exist, and it must be in the scope of the Data Flow task to which the data flow with the Row Count transformation belongs.</span></span>  
  
 <span data-ttu-id="59ad3-106">変換では、最後の行が変換を完了した後にのみ行数の値が変数に格納されます。</span><span class="sxs-lookup"><span data-stu-id="59ad3-106">The transformation stores the row count value in the variable only after the last row has passed through the transformation.</span></span> <span data-ttu-id="59ad3-107">そのため、変数の値は、行数変換を含むデータ フローで更新された値を使用できるタイミングでは更新されません。</span><span class="sxs-lookup"><span data-stu-id="59ad3-107">Therefore, the value of the variable is not updated in time to use the updated value in the data flow that contains the Row Count transformation.</span></span> <span data-ttu-id="59ad3-108">更新された変数は、別のデータ フローで使用できます。</span><span class="sxs-lookup"><span data-stu-id="59ad3-108">You can use the updated variable in a separate data flow.</span></span>  
  
 <span data-ttu-id="59ad3-109">この変換は 1 つの入力と 1 つの出力をとります。</span><span class="sxs-lookup"><span data-stu-id="59ad3-109">This transformation has one input and one output.</span></span> <span data-ttu-id="59ad3-110">エラー出力はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="59ad3-110">It does not support an error output.</span></span>  
  
## <a name="configuration-of-the-row-count-transformation"></a><span data-ttu-id="59ad3-111">行数変換の構成</span><span class="sxs-lookup"><span data-stu-id="59ad3-111">Configuration of the Row Count Transformation</span></span>  
 <span data-ttu-id="59ad3-112">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="59ad3-112">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="59ad3-113">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="59ad3-113">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="59ad3-114">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="59ad3-114">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="59ad3-115">Common Properties</span><span class="sxs-lookup"><span data-stu-id="59ad3-115">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="59ad3-116">変換のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="59ad3-116">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="59ad3-117">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="59ad3-117">Related Tasks</span></span>  
 <span data-ttu-id="59ad3-118">このコンポーネントのプロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](../set-the-properties-of-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59ad3-118">For information about how to set the properties of this component, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59ad3-119">参照</span><span class="sxs-lookup"><span data-stu-id="59ad3-119">See Also</span></span>  
 <span data-ttu-id="59ad3-120">[Integration Services &#40;SSIS&#41; の変数](../../integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="59ad3-120">[Integration Services &#40;SSIS&#41; Variables](../../integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="59ad3-121">[データ フロー](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="59ad3-121">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="59ad3-122">Integration Services の変換</span><span class="sxs-lookup"><span data-stu-id="59ad3-122">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  

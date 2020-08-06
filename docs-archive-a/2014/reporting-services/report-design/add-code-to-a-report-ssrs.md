---
title: レポートにコードを追加する (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- code [Reporting Services]
- custom code [Reporting Services]
- expressions [Reporting Services], code
- adding code
- reports [Reporting Services], code
ms.assetid: 00ef8fc6-99fe-49b2-8a22-7eb475881dc4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c1964e69d00e1a27da29ce8cfb73b7bee1bece7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717517"
---
# <a name="add-code-to-a-report-ssrs"></a><span data-ttu-id="f6253-102">レポートにコードを追加する (SSRS)</span><span class="sxs-lookup"><span data-stu-id="f6253-102">Add Code to a Report (SSRS)</span></span>
  <span data-ttu-id="f6253-103">どの式でも独自のカスタム コードを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f6253-103">In any expression, you can call your own custom code.</span></span> <span data-ttu-id="f6253-104">次の 2 つの方法でコードを提供できます。</span><span class="sxs-lookup"><span data-stu-id="f6253-104">You can provide code in the following two ways:</span></span>  
  
-   <span data-ttu-id="f6253-105">[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] で記述されたコードをレポートに直接埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="f6253-105">Embed code written in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] directly in your report.</span></span> <span data-ttu-id="f6253-106">コードが [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] または <xref:System.Math> ではない <xref:System.Convert> を参照する場合は、レポートへの参照を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6253-106">If your code refers to a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] that is not <xref:System.Math> or <xref:System.Convert>, you must add the reference to the report.</span></span> <span data-ttu-id="f6253-107">詳細については、「 [レポートにアセンブリへの参照を追加する &#40;SSRS&#41;](add-an-assembly-reference-to-a-report-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6253-107">For more information, see [Add an Assembly Reference to a Report &#40;SSRS&#41;](add-an-assembly-reference-to-a-report-ssrs.md).</span></span> <span data-ttu-id="f6253-108">コードから行うことのできる参照については、「[レポート デザイナーでカスタム コードやアセンブリを式から参照する &#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6253-108">For more information about other references you can make from your code, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).</span></span>  
  
-   <span data-ttu-id="f6253-109">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]を使用して、カスタム コード アセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="f6253-109">Provide a custom code assembly by using the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="f6253-110">カスタム アセンブリを指定する場合、レポートの作成場所のコンピューターとレポートを表示するレポート サーバーの両方にそれをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6253-110">If you provide a custom assembly, you must install it on both the computer where you author the report and the report server where you view the report.</span></span> <span data-ttu-id="f6253-111">詳細については、「 [レポートでのカスタム アセンブリの使用](../custom-assemblies/using-custom-assemblies-with-reports.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6253-111">For more information, see [Using Custom Assemblies with Reports](../custom-assemblies/using-custom-assemblies-with-reports.md).</span></span>  
  
### <a name="to-add-embedded-code-to-a-report"></a><span data-ttu-id="f6253-112">レポートに埋め込みコードを追加するには</span><span class="sxs-lookup"><span data-stu-id="f6253-112">To add embedded code to a report</span></span>  
  
1.  <span data-ttu-id="f6253-113">**[デザイン]** ビューで、デザイン画面のレポートの罫線の外を右クリックし、 **[レポートのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6253-113">In **Design** view, right-click the design surface outside the border of the report and click **Report Properties**.</span></span>  
  
2.  <span data-ttu-id="f6253-114">**[コード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6253-114">Click **Code**.</span></span>  
  
3.  <span data-ttu-id="f6253-115">**[カスタム コード]** でコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="f6253-115">In **Custom code**, type the code.</span></span> <span data-ttu-id="f6253-116">コード内にエラーがあると、レポートの実行時に警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f6253-116">Errors in the code produce warnings when the report runs.</span></span> <span data-ttu-id="f6253-117">次の例では、" `ChangeWord` " という単語を "`Bike`" で置き換える`Bicycle`という名前のカスタム関数が作成されます。</span><span class="sxs-lookup"><span data-stu-id="f6253-117">The following example creates a custom function named `ChangeWord` that replaces the word "`Bike`" with "`Bicycle`".</span></span>  
  
    ```  
    Public Function ChangeWord(ByVal s As String) As String  
       Dim strBuilder As New System.Text.StringBuilder(s)  
       If s.Contains("Bike") Then  
          strBuilder.Replace("Bike", "Bicycle")  
          Return strBuilder.ToString()  
          Else : Return s  
       End If  
    End Function  
    ```  
  
4.  <span data-ttu-id="f6253-118">次の例は、式で Category という名前のデータセット フィールドをこの関数に渡す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f6253-118">The following example shows how to pass a dataset field named Category to this function in an expression:</span></span>  
  
    ```  
    =Code.ChangeWord(Fields!Category.Value)  
    ```  
  
     <span data-ttu-id="f6253-119">この式をカテゴリの値を表示するテーブル セルに追加すると、"Bike" という単語がその行のデータセット フィールドに現れるたびに、テーブル セルの値は "Bicycle" という単語を表示します。</span><span class="sxs-lookup"><span data-stu-id="f6253-119">If you add this expression to a table cell that displays category values, whenever the word "Bike" is in the dataset field for that row, the table cell value displays the word "Bicycle" instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6253-120">参照</span><span class="sxs-lookup"><span data-stu-id="f6253-120">See Also</span></span>  
 <span data-ttu-id="f6253-121">[[コード] ([レポートのプロパティ] ダイアログ ボックス)](../report-properties-dialog-box-code.md) </span><span class="sxs-lookup"><span data-stu-id="f6253-121">[Report Properties Dialog Box, Code](../report-properties-dialog-box-code.md) </span></span>  
 <span data-ttu-id="f6253-122">[式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f6253-122">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f6253-123">Parameters コレクションの参照 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f6253-123">Parameters Collection References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-parameters-collection-references-report-builder.md)  
  
  

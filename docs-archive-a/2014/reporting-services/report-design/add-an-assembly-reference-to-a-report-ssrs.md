---
title: レポートにアセンブリへの参照を追加する (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- code [Reporting Services]
- custom assemblies [Reporting Services], referencing
- custom code [Reporting Services]
- adding assembly references
- assemblies [Reporting Services], references
ms.assetid: 0a03939e-48ce-4c30-b227-98533f2e0ccb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 23dda0c65589e55849f906c621e42ce70f0d7ab5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643180"
---
# <a name="add-an-assembly-reference-to-a-report-ssrs"></a><span data-ttu-id="da706-102">レポートにアセンブリへの参照を追加する (SSRS)</span><span class="sxs-lookup"><span data-stu-id="da706-102">Add an Assembly Reference to a Report (SSRS)</span></span>
  <span data-ttu-id="da706-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] または [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] にない <xref:System.Math> <xref:System.Convert> クラスへの参照を含むカスタム コードを埋め込む場合は、レポート プロセッサで名前を解決できるように、レポートへのアセンブリ参照を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="da706-103">When you embed custom code that contains references to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] classes that are not in <xref:System.Math> or <xref:System.Convert>, you must provide an assembly reference to the report so that the report processor can resolve the names.</span></span> <span data-ttu-id="da706-104">詳細については、「[レポートにコードを追加する (SSRS)](add-code-to-a-report-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da706-104">For more information, see [Add Code to a Report &#40;SSRS&#41;](add-code-to-a-report-ssrs.md).</span></span>  
  
### <a name="to-add-an-assembly-reference-to-a-report"></a><span data-ttu-id="da706-105">レポートにアセンブリへの参照を追加するには</span><span class="sxs-lookup"><span data-stu-id="da706-105">To add an assembly reference to a report</span></span>  
  
1.  <span data-ttu-id="da706-106">**[デザイン]** ビューで、デザイン画面のレポートの罫線の外を右クリックし、 **[レポートのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="da706-106">In **Design** view, right-click the design surface outside the border of the report and click **Report Properties**.</span></span>  
  
2.  <span data-ttu-id="da706-107">**[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="da706-107">Click **References**.</span></span>  
  
3.  <span data-ttu-id="da706-108">**[アセンブリの追加または削除]** で **[追加]** をクリックしてから、参照ボタンをクリックし、アセンブリを参照します。</span><span class="sxs-lookup"><span data-stu-id="da706-108">In **Add or remove assemblies**, click **Add** and then click the ellipsis button to browse to the assembly.</span></span>  
  
4.  <span data-ttu-id="da706-109">**[クラスの追加または削除]** で **[追加]** をクリックしてから、クラスの名前を入力し、レポート内で使用するインスタンス名を指定します。</span><span class="sxs-lookup"><span data-stu-id="da706-109">In **Add or remove classes**, click **Add** and then type name of the class and provide an instance name to use within the report.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="da706-110">インスタンスベースのメンバーにのみ、クラスおよびインスタンスの名前を指定してください。</span><span class="sxs-lookup"><span data-stu-id="da706-110">Specify a class and instance name only for instance-based members.</span></span> <span data-ttu-id="da706-111">**[クラス]** の一覧に静的メンバーを指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="da706-111">Do not specify static members in the **Classes** list.</span></span> <span data-ttu-id="da706-112">詳細については、「 [レポート デザイナーでカスタム コードやアセンブリを式から参照する (SSRS)](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)を表しています。</span><span class="sxs-lookup"><span data-stu-id="da706-112">For more information, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="da706-113">参照</span><span class="sxs-lookup"><span data-stu-id="da706-113">See Also</span></span>  
 <span data-ttu-id="da706-114">[レポートでのカスタム アセンブリの使用](../custom-assemblies/using-custom-assemblies-with-reports.md) </span><span class="sxs-lookup"><span data-stu-id="da706-114">[Using Custom Assemblies with Reports](../custom-assemblies/using-custom-assemblies-with-reports.md) </span></span>  
 <span data-ttu-id="da706-115">[[参照] ([レポートのプロパティ] ダイアログ ボックス)](../report-properties-dialog-box-references.md)</span><span class="sxs-lookup"><span data-stu-id="da706-115">[Report Properties Dialog Box, References](../report-properties-dialog-box-references.md)</span></span>  
  
  

---
title: XML 出力ファイル形式 (ssbdiagnose) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- XML output file format [ssbdiagnose]
- ssbdiagnose
ms.assetid: 3ceb991b-6f15-4504-8828-de5adf448bc5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 612b317f7220f502faf1adc82cf9c1dcc8bc20a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720588"
---
# <a name="xml-output-file-format-ssbdiagnose"></a><span data-ttu-id="32c56-102">XML 出力ファイルの形式 (ssbdiagnose)</span><span class="sxs-lookup"><span data-stu-id="32c56-102">XML Output File Format (ssbdiagnose)</span></span>
  <span data-ttu-id="32c56-103">**ssbdiagnose** ユーティリティは、 **-XML** スイッチを指定して実行した場合、その出力を XML ファイルとして配布します。</span><span class="sxs-lookup"><span data-stu-id="32c56-103">The **ssbdiagnose** utility delivers its output as an XML file when you run it with the **-XML** switch.</span></span> <span data-ttu-id="32c56-104">XML 出力ファイルでは、ヘッダー情報と、分析された [!INCLUDE[ssSB](../../includes/sssb-md.md)] の構成またはメッセージ交換で検出されたエラーが示されます。</span><span class="sxs-lookup"><span data-stu-id="32c56-104">The XML output file lists header information and the errors that it found in the [!INCLUDE[ssSB](../../includes/sssb-md.md)] configuration or conversation that was analyzed.</span></span> <span data-ttu-id="32c56-105">ファイルに示されたエラーを分析して報告するためのアプリケーションを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="32c56-105">You can write an application to analyze or report on the errors listed in the file.</span></span> <span data-ttu-id="32c56-106">また、XML ファイルを XML Notepad などの一般的な XML エディターで表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="32c56-106">Or, you can view the XML file in a general XML editor, such as XML Notepad.</span></span>  
  
 <span data-ttu-id="32c56-107">**ssbdiangose** の出力ファイルには、2 種類の子を持つ DiagnosticInformation ルート要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="32c56-107">An **ssbdiangose** output file contains a DiagnosticInformation root element with two child types:</span></span>  
  
-   <span data-ttu-id="32c56-108">ヘッダー情報を含む Banner 要素。</span><span class="sxs-lookup"><span data-stu-id="32c56-108">A Banner element with header information.</span></span>  
  
-   <span data-ttu-id="32c56-109">**ssbdiagnose**によって報告される各問題を示す Issue 要素。</span><span class="sxs-lookup"><span data-stu-id="32c56-109">An Issue element for each issue that is reported by **ssbdiagnose**.</span></span>  
  
## <a name="diagnosticinformation-root-element"></a><span data-ttu-id="32c56-110">DiagnosticInformation ルート要素 (ssbdiagnose)</span><span class="sxs-lookup"><span data-stu-id="32c56-110">DiagnosticInformation Root Element</span></span>  
  
-   [<span data-ttu-id="32c56-111">DiagnosticInformation 要素 &#40;ssbdiagnose&#41;</span><span class="sxs-lookup"><span data-stu-id="32c56-111">DiagnosticInformation Element &#40;ssbdiagnose&#41;</span></span>](diagnosticinformation-element-ssbdiagnose.md)  
  
## <a name="banner-element"></a><span data-ttu-id="32c56-112">Banner 要素</span><span class="sxs-lookup"><span data-stu-id="32c56-112">Banner Element</span></span>  
  
-   [<span data-ttu-id="32c56-113">Banner 要素 &#40;ssbdiagnose&#41;</span><span class="sxs-lookup"><span data-stu-id="32c56-113">Banner Element &#40;ssbdiagnose&#41;</span></span>](banner-element-ssbdiagnose.md)  
  
## <a name="issue-element"></a><span data-ttu-id="32c56-114">Issue 要素</span><span class="sxs-lookup"><span data-stu-id="32c56-114">Issue Element</span></span>  
  
-   [<span data-ttu-id="32c56-115">Issue 要素 &#40;ssbdiagnose&#41;</span><span class="sxs-lookup"><span data-stu-id="32c56-115">Issue Element &#40;ssbdiagnose&#41;</span></span>](issue-element-ssbdiagnose.md)  
  
## <a name="see-also"></a><span data-ttu-id="32c56-116">参照</span><span class="sxs-lookup"><span data-stu-id="32c56-116">See Also</span></span>  
 [<span data-ttu-id="32c56-117">ssbdiagnose ユーティリティ &#40;Service Broker&#41;</span><span class="sxs-lookup"><span data-stu-id="32c56-117">ssbdiagnose Utility &#40;Service Broker&#41;</span></span>](ssbdiagnose-utility-service-broker.md)  
  
  

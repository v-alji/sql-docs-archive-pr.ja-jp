---
title: Analysis Services プロジェクトの XML の表示 (SSDT) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- projects [Analysis Services], viewing XML
ms.assetid: dd1a4bc6-57b5-47df-8619-09f921aa6351
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1c320145be2073c741498bed0f10732ac8d528e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740512"
---
# <a name="view-the-xml-for-an-analysis-services-project-ssdt"></a><span data-ttu-id="69d0b-102">Analysis Services のプロジェクトでの XML の表示 (SSDT)</span><span class="sxs-lookup"><span data-stu-id="69d0b-102">View the XML for an Analysis Services Project (SSDT)</span></span>
  <span data-ttu-id="69d0b-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のデータベースをプロジェクト モードで操作している場合は、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] によって各オブジェクトの XML 定義がプロジェクト フォルダー内に作成されます。</span><span class="sxs-lookup"><span data-stu-id="69d0b-103">When you are working with an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in project mode, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] creates an XML definition for each object within the project folder.</span></span> <span data-ttu-id="69d0b-104">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]内で各オブジェクトの XML ファイルの内容を見ることができます。</span><span class="sxs-lookup"><span data-stu-id="69d0b-104">You can view the contents of the XML file for each object within [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="69d0b-105">また、XML ファイルを直接編集することもできますが、変更によって XML を [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で読み取れなくなる可能性があるため、ほとんどの状況ではお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="69d0b-105">You can also edit the XML file directly; however, this is not recommended in most circumstances as you may make changes that make the XML unreadable by [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="69d0b-106">オブジェクトごとにファイルが異なるため、プロジェクト全体の xml コードは表示できませんが、各オブジェクトのコードを確認します。</span><span class="sxs-lookup"><span data-stu-id="69d0b-106">You cannot view the xml code for an entire project, but rather you view the code for each object because a separate file exists for each object.</span></span> <span data-ttu-id="69d0b-107">プロジェクト全体のコードを表示する唯一の方法は、プロジェクトをビルドし、asdatabase ファイルで ASSL コードを表示することです。 \<project name></span><span class="sxs-lookup"><span data-stu-id="69d0b-107">The only way to view the code for an entire project is to build the project and view the ASSL code in the \<project name>.asdatabase file.</span></span>  
  
### <a name="to-view-the-xml-code-for-an-object"></a><span data-ttu-id="69d0b-108">オブジェクトの XML コードを表示するには</span><span class="sxs-lookup"><span data-stu-id="69d0b-108">To view the XML code for an object</span></span>  
  
1.  <span data-ttu-id="69d0b-109">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="69d0b-109">Open the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="69d0b-110">ソリューション エクスプローラーでオブジェクトを右クリックし、 **[コードの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="69d0b-110">Right-click the object in Solution Explorer and then click **View Code**.</span></span>  
  
     <span data-ttu-id="69d0b-111">オブジェクトの XML コードが [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]に表示されます。</span><span class="sxs-lookup"><span data-stu-id="69d0b-111">The XML code for the object appears in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69d0b-112">参照</span><span class="sxs-lookup"><span data-stu-id="69d0b-112">See Also</span></span>  
 [<span data-ttu-id="69d0b-113">Analysis Services プロジェクトのビルド &#40;SSDT&#41;</span><span class="sxs-lookup"><span data-stu-id="69d0b-113">Build Analysis Services Projects &#40;SSDT&#41;</span></span>](build-analysis-services-projects-ssdt.md)  
  
  

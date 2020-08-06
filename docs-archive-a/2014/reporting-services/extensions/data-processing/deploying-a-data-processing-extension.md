---
title: データ処理拡張機能の配置 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: e5c0b5a9-1386-47cb-aade-96653ecfaa54
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 84fc2d2853ce7a6aae77f313ef0f4026ad2f35cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741605"
---
# <a name="deploying-a-data-processing-extension"></a><span data-ttu-id="d0b22-102">データ処理拡張機能の配置</span><span class="sxs-lookup"><span data-stu-id="d0b22-102">Deploying a Data Processing Extension</span></span>
  <span data-ttu-id="d0b22-103">ご自分の [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のデータ処理拡張機能は、作成して [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ライブラリにコンパイルした後、レポート サーバーおよびレポート デザイナーで検出できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0b22-103">Once you have written and compiled your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension into a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] library, you need to make it discoverable by the report server and by Report Designer.</span></span> <span data-ttu-id="d0b22-104">これは、適切なディレクトリに拡張機能をコピーし、適切な [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 構成ファイルにエントリを追加するだけで簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="d0b22-104">This is as easy as copying the extension to the appropriate directories and adding entries to the appropriate [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] configuration files.</span></span>  
  
## <a name="configuration-file-extension-element"></a><span data-ttu-id="d0b22-105">構成ファイルの Extension 要素</span><span class="sxs-lookup"><span data-stu-id="d0b22-105">Configuration-File Extension Element</span></span>  
 <span data-ttu-id="d0b22-106">レポート サーバーまたはレポート デザイナーに配置するデータ処理拡張機能は、構成ファイルに **Extension** 要素として入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0b22-106">Data processing extensions that you deploy to the report server or Report Designer need to be entered as **Extension** elements in the configuration files.</span></span> <span data-ttu-id="d0b22-107">構成ファイルは、レポート サーバーの場合は RSReportServer.config、レポート デザイナーの場合は RSReportDesigner.config です。</span><span class="sxs-lookup"><span data-stu-id="d0b22-107">These files are RSReportServer.config for the report server and RSReportDesigner.config for Report Designer.</span></span>  
  
 <span data-ttu-id="d0b22-108">次の表では、データ処理拡張機能の **Extension** 要素の属性について説明します。</span><span class="sxs-lookup"><span data-stu-id="d0b22-108">The following table describes the attributes for the **Extension** element for data processing extensions.</span></span>  
  
|<span data-ttu-id="d0b22-109">Attribute</span><span class="sxs-lookup"><span data-stu-id="d0b22-109">Attribute</span></span>|<span data-ttu-id="d0b22-110">説明</span><span class="sxs-lookup"><span data-stu-id="d0b22-110">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="d0b22-111">拡張機能の一意な名前。たとえば、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ処理拡張機能に対して "SQL"、OLE DB データ処理拡張機能に対して "OLEDB"。</span><span class="sxs-lookup"><span data-stu-id="d0b22-111">A unique name for the extension, for example, "SQL" for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data processing extension or "OLEDB" for the OLE DB data processing extension.</span></span> <span data-ttu-id="d0b22-112">`Name` 属性の最大文字数は 255 文字です。</span><span class="sxs-lookup"><span data-stu-id="d0b22-112">The maximum length for the `Name` attribute is 255 characters.</span></span> <span data-ttu-id="d0b22-113">名前は、構成ファイルの **Extension** 要素内にあるすべてのエントリの間で一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0b22-113">The name must be unique among all entries within the **Extension** element of a configuration file.</span></span>|  
|`Type`|<span data-ttu-id="d0b22-114">アセンブリの名前と共に完全修飾名前空間を含むコンマ区切りの一覧。</span><span class="sxs-lookup"><span data-stu-id="d0b22-114">A comma-separated list that includes the fully qualified namespace along with the name of the assembly.</span></span>|  
|`Visible`|<span data-ttu-id="d0b22-115">`false` の値は、データ処理拡張機能がユーザー インターフェイスに表示されないことを示します。</span><span class="sxs-lookup"><span data-stu-id="d0b22-115">A value of `false` indicates that the data processing extension should not be visible in user interfaces.</span></span> <span data-ttu-id="d0b22-116">この属性が指定されない場合、既定値は `true` になります。</span><span class="sxs-lookup"><span data-stu-id="d0b22-116">If the attribute is not included, the default value is `true`.</span></span>|  
  
 <span data-ttu-id="d0b22-117">RSReportServer.config ファイルまたは RSReportDesigner.config ファイルの詳細については、「[Reporting Services 構成ファイル](../../report-server/reporting-services-configuration-files.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0b22-117">For more information about the RSReportServer.config or RSReportDesigner.config files, see [Reporting Services Configuration Files](../../report-server/reporting-services-configuration-files.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d0b22-118">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d0b22-118">In This Section</span></span>  
  
|<span data-ttu-id="d0b22-119">トピック</span><span class="sxs-lookup"><span data-stu-id="d0b22-119">Topic</span></span>|<span data-ttu-id="d0b22-120">説明</span><span class="sxs-lookup"><span data-stu-id="d0b22-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d0b22-121">データ処理拡張機能をレポート サーバーに配置する方法</span><span class="sxs-lookup"><span data-stu-id="d0b22-121">How to: Deploy a Data Processing Extension to a Report Server</span></span>](deploying-a-data-processing-extension-to-a-report-server.md)|<span data-ttu-id="d0b22-122">レポート サーバーにデータ処理拡張機能を配置する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d0b22-122">Describes how to deploy your data processing extension to a report server.</span></span>|  
|[<span data-ttu-id="d0b22-123">データ処理拡張機能をレポート デザイナーに配置する方法</span><span class="sxs-lookup"><span data-stu-id="d0b22-123">How to: Deploy a Data Processing Extension to Report Designer</span></span>](deploying-a-data-processing-extension-to-report-designer.md)|<span data-ttu-id="d0b22-124">レポート デザイナーにデータ処理拡張機能を配置する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d0b22-124">Describes how to deploy your data processing extension to Report Designer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0b22-125">参照</span><span class="sxs-lookup"><span data-stu-id="d0b22-125">See Also</span></span>  
 <span data-ttu-id="d0b22-126">[Reporting Services 拡張機能](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="d0b22-126">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="d0b22-127">[データ処理拡張機能の実装](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="d0b22-127">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="d0b22-128">Reporting Services 拡張機能ライブラリ</span><span class="sxs-lookup"><span data-stu-id="d0b22-128">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  

---
title: Excel 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- files [Integration Services], connections
- connections [Integration Services], Excel
- Excel [Integration Services]
- connection managers [Integration Services], Excel
ms.assetid: 667419f2-74fb-4b50-b963-9197d1368cda
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7561361c6d4ab7e22282b25367906aa4b75e5bc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640202"
---
# <a name="excel-connection-manager"></a><span data-ttu-id="4c878-102">Excel 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="4c878-102">Excel Connection Manager</span></span>
  <span data-ttu-id="4c878-103">Excel 接続マネージャーを使用すると、パッケージは既存の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel ブック ファイルに接続できます。</span><span class="sxs-lookup"><span data-stu-id="4c878-103">An Excel connection manager enables a package to connect to an existing [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel workbook file.</span></span> <span data-ttu-id="4c878-104">Excel ソースおよび excel 変換先には、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] excel 接続マネージャーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="4c878-104">The Excel source and the Excel destination that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] include use the Excel connection manager.</span></span>  
  
 <span data-ttu-id="4c878-105">Excel 接続マネージャーをパッケージに追加するときに、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] により、実行時に Excel 接続として解決される接続マネージャーを作成し、接続マネージャーのプロパティを設定して、接続マネージャーをパッケージの `Connections` コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="4c878-105">When you add an Excel connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that is resolved as an Excel connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span>  
  
 <span data-ttu-id="4c878-106">接続マネージャーの `ConnectionManagerType` プロパティは、`EXCEL` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="4c878-106">The `ConnectionManagerType` property of the connection manager is set to `EXCEL`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4c878-107">パスワードで保護された Excel ファイルには接続できません。</span><span class="sxs-lookup"><span data-stu-id="4c878-107">You cannot connect to a password-protected Excel file.</span></span>  
  
## <a name="configuration-of-the-excel-connection-manager"></a><span data-ttu-id="4c878-108">Excel 接続マネージャーの構成</span><span class="sxs-lookup"><span data-stu-id="4c878-108">Configuration of the Excel Connection Manager</span></span>  
 <span data-ttu-id="4c878-109">Excel 接続マネージャーは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="4c878-109">You can configure the Excel connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="4c878-110">Excel ブック ファイルのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="4c878-110">Specify the path of the Excel workbook file.</span></span>  
  
-   <span data-ttu-id="4c878-111">ファイルの作成に使用した Excel のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="4c878-111">Specify the version of Excel that was used to create the file.</span></span>  
  
-   <span data-ttu-id="4c878-112">選択したワークシート内または範囲内でアクセスするデータの最初の行に、列名が格納されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="4c878-112">Indicate whether the first row of accessed data in the selected worksheets or ranges contains column names.</span></span>  
  
 <span data-ttu-id="4c878-113">Excel ソースによって Excel 接続マネージャーが使用された場合は、抽出したデータに列名が含められます。</span><span class="sxs-lookup"><span data-stu-id="4c878-113">If the Excel connection manager is used by an Excel source, the column names are included with the extracted data.</span></span> <span data-ttu-id="4c878-114">Excel 変換先によって使用された場合は、出力されたデータに列名が含められます。</span><span class="sxs-lookup"><span data-stu-id="4c878-114">If it is used by an Excel destination, the column names are included in the written data.</span></span>  
  
 <span data-ttu-id="4c878-115">Excel 接続マネージャーは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet 4.0 用の OLE DB プロバイダーと、それをサポートする EXCEL ISAM (インデックス付きシーケンシャルアクセス方式) ドライバーを使用して、excel データソースへの接続とデータの読み書きを行います。</span><span class="sxs-lookup"><span data-stu-id="4c878-115">The Excel connection manager uses the [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Jet 4.0 and its supporting Excel ISAM (Indexed Sequential Access Method) driver to connect and read and write data to Excel data sources.</span></span> <span data-ttu-id="4c878-116">Excel ソースおよび excel 変換先で使用する場合のこのプロバイダーとドライバーの動作の詳細については、「 [Excel ソース](../data-flow/excel-source.md)および Excel[変換先](../data-flow/excel-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c878-116">For more information about the behavior of this provider and driver when used with Excel sources and Excel destinations, see [Excel Source](../data-flow/excel-source.md) and [Excel Destination](../data-flow/excel-destination.md).</span></span>  
  
 <span data-ttu-id="4c878-117">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="4c878-117">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="4c878-118">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、「 [Excel 接続マネージャー](../excel-connection-manager-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c878-118">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [Excel Connection Manager Editor](../excel-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="4c878-119">プログラムによる接続マネージャーの構成については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」と「 [プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)に設定されます。</span><span class="sxs-lookup"><span data-stu-id="4c878-119">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
 <span data-ttu-id="4c878-120">Excel ファイルのグループによるループ処理については、「 [Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する](../control-flow/foreach-loop-container.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4c878-120">For information about looping through a group of Excel files, see [Loop through Excel Files and Tables by Using a Foreach Loop Container](../control-flow/foreach-loop-container.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="4c878-121">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="4c878-121">Related Tasks</span></span>  
  
-   [<span data-ttu-id="4c878-122">Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する</span><span class="sxs-lookup"><span data-stu-id="4c878-122">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](../control-flow/foreach-loop-container.md)  
  
-   [<span data-ttu-id="4c878-123">SQL Server Integration Services (SSIS) を使用して、Excel からデータをインポートする、または Excel にデータをエクスポートする</span><span class="sxs-lookup"><span data-stu-id="4c878-123">Import data from Excel or export data to Excel with SQL Server Integration Services (SSIS)</span></span>](../load-data-to-from-excel-with-ssis.md)
  
  

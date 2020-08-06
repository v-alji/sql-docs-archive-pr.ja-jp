---
title: Excel 接続マネージャーエディター |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.excelconnection.f1
helpviewer_keywords:
- Excel Connection Manager Editor
ms.assetid: 7ff097e4-cafb-4885-a898-05b2a46628c1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7f66de13b710e5ccb577e6f2d67c215572e34767
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641764"
---
# <a name="excel-connection-manager-editor"></a><span data-ttu-id="2f3ef-102">Excel 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="2f3ef-102">Excel Connection Manager Editor</span></span>
  <span data-ttu-id="2f3ef-103">**[Excel 接続マネージャー]** ダイアログ ボックスを使用すると、既存または新規の [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] ブック ファイルへの接続を追加できます。</span><span class="sxs-lookup"><span data-stu-id="2f3ef-103">Use the **Excel Connection Manager Editor** dialog box to add a connection to an existing or a new [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] workbook file.</span></span>  
  
 <span data-ttu-id="2f3ef-104">Excel 接続マネージャーの詳細については、「 [Excel Connection Manager](connection-manager/excel-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f3ef-104">To learn more about the Excel connection manager, see [Excel Connection Manager](connection-manager/excel-connection-manager.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2f3ef-105">パスワードで保護された Excel ファイルには接続できません。</span><span class="sxs-lookup"><span data-stu-id="2f3ef-105">You cannot connect to a password-protected Excel file.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2f3ef-106">Options</span><span class="sxs-lookup"><span data-stu-id="2f3ef-106">Options</span></span>  
 <span data-ttu-id="2f3ef-107">**[Excel ファイル パス]**</span><span class="sxs-lookup"><span data-stu-id="2f3ef-107">**Excel file path**</span></span>  
 <span data-ttu-id="2f3ef-108">既存または新規の Excel ブック ファイル (.xls) のパスおよびファイル名を入力します。</span><span class="sxs-lookup"><span data-stu-id="2f3ef-108">Type the path and file name of an existing or a new Excel workbook file (.xls).</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="2f3ef-109">Excel**変換先エディター**では、存在しないファイルをポイントする**excel 接続**を選択すると、excel ファイルが自動的に作成されます。その後、[ **excel シートの名前**] で [**新規**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f3ef-109">The **Excel Destination Editor** automatically creates the Excel file when you select an **Excel Connection** that points to a new/non-existent file and then click **New** for **Name of the Excel Sheet**.</span></span>  
  
 <span data-ttu-id="2f3ef-110">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="2f3ef-110">**Browse**</span></span>  
 <span data-ttu-id="2f3ef-111">**[開く]** ダイアログ ボックスを使用して、Excel ファイルが存在するフォルダー、または新しいファイルを作成するフォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="2f3ef-111">Use the **Open** dialog box to navigate to the folder in which the excel file exists or where you want to create the new file.</span></span>  
  
 <span data-ttu-id="2f3ef-112">**Excel のバージョン**</span><span class="sxs-lookup"><span data-stu-id="2f3ef-112">**Excel version**</span></span>  
 <span data-ttu-id="2f3ef-113">ファイルを作成するために使用した Microsoft Excel のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="2f3ef-113">Specify the version of Microsoft Excel that was used to create the file.</span></span>  
  
|<span data-ttu-id="2f3ef-114">オプション</span><span class="sxs-lookup"><span data-stu-id="2f3ef-114">Option</span></span>|<span data-ttu-id="2f3ef-115">説明</span><span class="sxs-lookup"><span data-stu-id="2f3ef-115">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="2f3ef-116">[Microsoft Excel 97-2005]</span><span class="sxs-lookup"><span data-stu-id="2f3ef-116">Excel 97-2003</span></span>|<span data-ttu-id="2f3ef-117">ファイルは Excel 97 以降を使用して作成されています。</span><span class="sxs-lookup"><span data-stu-id="2f3ef-117">File was created using Excel 97 or later.</span></span>|  
|<span data-ttu-id="2f3ef-118">Excel 3.0</span><span class="sxs-lookup"><span data-stu-id="2f3ef-118">Excel 3.0</span></span>|<span data-ttu-id="2f3ef-119">ファイルは Excel 3.0 を使用して作成されました。</span><span class="sxs-lookup"><span data-stu-id="2f3ef-119">File was created using Excel 3.0.</span></span>|  
|<span data-ttu-id="2f3ef-120">Excel 4.0</span><span class="sxs-lookup"><span data-stu-id="2f3ef-120">Excel 4.0</span></span>|<span data-ttu-id="2f3ef-121">ファイルは Excel 4.0 を使用して作成されています。</span><span class="sxs-lookup"><span data-stu-id="2f3ef-121">File was created using Excel 4.0.</span></span>|  
|<span data-ttu-id="2f3ef-122">Excel 5.0</span><span class="sxs-lookup"><span data-stu-id="2f3ef-122">Excel 5.0</span></span>|<span data-ttu-id="2f3ef-123">ファイルは Excel 95 (7.0) を使用して作成されています。</span><span class="sxs-lookup"><span data-stu-id="2f3ef-123">File was created using Excel 95 (7.0).</span></span>|  
  
 <span data-ttu-id="2f3ef-124">**最初の行に列名がある**</span><span class="sxs-lookup"><span data-stu-id="2f3ef-124">**First row has column names**</span></span>  
 <span data-ttu-id="2f3ef-125">選択されているワークシートのデータの 1 行目に列名が含まれているかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="2f3ef-125">Specify whether the first row of data in the selected worksheet contains column names.</span></span> <span data-ttu-id="2f3ef-126">このオプションの既定値は **[true]** です。</span><span class="sxs-lookup"><span data-stu-id="2f3ef-126">The default value of this option is **True**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f3ef-127">参照</span><span class="sxs-lookup"><span data-stu-id="2f3ef-127">See Also</span></span>  
 <span data-ttu-id="2f3ef-128">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="2f3ef-128">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="2f3ef-129">Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する</span><span class="sxs-lookup"><span data-stu-id="2f3ef-129">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](control-flow/foreach-loop-container.md)  
  
  

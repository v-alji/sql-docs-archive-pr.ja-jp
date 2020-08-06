---
title: Azure BLOB のダウンロード タスク | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobdltask.f1
- sql11.dts.designer.afpblobdltask.f1
ms.assetid: 8a63bf44-71be-456d-9a5c-be7c31aff065
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e2f61260b1fceaad3c27a0ce6ab6af28b15582bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713394"
---
# <a name="azure-blob-download-task"></a><span data-ttu-id="7e914-102">Azure BLOB のダウンロード タスク</span><span class="sxs-lookup"><span data-stu-id="7e914-102">Azure Blob Download Task</span></span>
  <span data-ttu-id="7e914-103">Azure BLOB のダウンロード タスクを使うと、SSIS パッケージで Azure BLOB ストレージからファイルをダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="7e914-103">The Azure Blob Download Task enables an SSIS package to download files from an Azure blob storage.</span></span>   
<span data-ttu-id="7e914-104">**Azure BLOB のダウンロード タスク**を追加するには、SSIS デザイナーにドラッグ アンド ドロップし、ダブルクリックまたは右クリックして、 **[編集]** をクリックすると、次の **[Azure BLOB ダウンロード タスク エディター]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e914-104">To add an **Azure Blob Download Task**, drag-drop it to the SSIS Designer, and double-click or right-click and click **Edit** to see the following **Azure Blob Download Task Editor** dialog box.</span></span>  
  
 <span data-ttu-id="7e914-105">次の表で、このダイアログ ボックスの各フィールドを説明します。</span><span class="sxs-lookup"><span data-stu-id="7e914-105">The following table provides description for the fields in this dialog box.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7e914-106">**フィールド**</span><span class="sxs-lookup"><span data-stu-id="7e914-106">**Field**</span></span>|<span data-ttu-id="7e914-107">**説明**</span><span class="sxs-lookup"><span data-stu-id="7e914-107">**Description**</span></span>|  
|<span data-ttu-id="7e914-108">AzureStorageConnection</span><span class="sxs-lookup"><span data-stu-id="7e914-108">AzureStorageConnection</span></span>|<span data-ttu-id="7e914-109">既存の Azure ストレージ接続マネージャーを指定するか、Azure ストレージ アカウントを参照する新しい接続マネージャーを作成します。この接続マネージャーは、BLOB ファイルがホストされている場所をポイントします。</span><span class="sxs-lookup"><span data-stu-id="7e914-109">Specify an existing Azure Storage Connection Manager or create a new one that refers to an Azure Storage Account, which points to where the blob files are hosted.</span></span>|  
|<span data-ttu-id="7e914-110">BlobContainer</span><span class="sxs-lookup"><span data-stu-id="7e914-110">BlobContainer</span></span>|<span data-ttu-id="7e914-111">ダウンロードする BLOB ファイルを含む BLOB コンテナーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="7e914-111">Specifies the name of the blob container that contains the blob files to be downloaded.</span></span>|  
|<span data-ttu-id="7e914-112">BlobDirectory</span><span class="sxs-lookup"><span data-stu-id="7e914-112">BlobDirectory</span></span>|<span data-ttu-id="7e914-113">ダウンロードする BLOB ファイルを含む BLOB ディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="7e914-113">Specifies the blob directory that contains the blob files to be downloaded.</span></span> <span data-ttu-id="7e914-114">BLOB ディレクトリは仮想階層構造です。</span><span class="sxs-lookup"><span data-stu-id="7e914-114">The blob directory is a virtual hierarchical structure.</span></span>|  
|<span data-ttu-id="7e914-115">LocalDirectory</span><span class="sxs-lookup"><span data-stu-id="7e914-115">LocalDirectory</span></span>|<span data-ttu-id="7e914-116">ダウンロードした BLOB ファイルが格納されるローカル ディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="7e914-116">Specifies the local directory where the downloaded blob files will be stored.</span></span>|  
|<span data-ttu-id="7e914-117">FileName</span><span class="sxs-lookup"><span data-stu-id="7e914-117">FileName</span></span>|<span data-ttu-id="7e914-118">指定された名前のパターンを使用したファイルを選択するための名前フィルターを指定します。</span><span class="sxs-lookup"><span data-stu-id="7e914-118">Specifies a name filter to select files with the specified name pattern.</span></span> <span data-ttu-id="7e914-119">例:</span><span class="sxs-lookup"><span data-stu-id="7e914-119">E.g.</span></span> <span data-ttu-id="7e914-120">MySheet\*.xls\* には、MySheet001.xls や MySheetABC.xlsx などのファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="7e914-120">MySheet\*.xls\* includes files such as MySheet001.xls and MySheetABC.xlsx.</span></span>|  
|<span data-ttu-id="7e914-121">TimeRangeFrom/TimeRangeTo</span><span class="sxs-lookup"><span data-stu-id="7e914-121">TimeRangeFrom/TimeRangeTo</span></span>|<span data-ttu-id="7e914-122">時間範囲フィルターを指定します。</span><span class="sxs-lookup"><span data-stu-id="7e914-122">Specifies a time range filter.</span></span> <span data-ttu-id="7e914-123">**TimeRangeFrom** から **TimeRangeTo** までの間に変更されたファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="7e914-123">Files modified after **TimeRangeFrom** and before **TimeRangeTo** will be included.</span></span>|  
  
  

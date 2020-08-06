---
title: Azure BLOB のアップロード タスク | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobuptask.f1
- sql11.dts.designer.afpblobuptask.f1
ms.assetid: 6ea068b0-4cd8-45b5-b89d-09b8f25040c0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0ca15c5a77a2694293981121f4e5927be8ec0e1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713393"
---
# <a name="azure-blob-upload-task"></a><span data-ttu-id="930be-102">Azure BLOB のアップロード タスク</span><span class="sxs-lookup"><span data-stu-id="930be-102">Azure Blob Upload Task</span></span>
  <span data-ttu-id="930be-103">Azure BLOB のアップロード タスクを使うと、SSIS パッケージで Azure BLOB ストレージにファイルをアップロードできます。</span><span class="sxs-lookup"><span data-stu-id="930be-103">The Azure Blob Upload Task enables an SSIS package to upload files to an Azure blob storage.</span></span>   
<span data-ttu-id="930be-104">**Azure BLOB のアップロード タスク**を追加するには、SSIS デザイナーにドラッグ アンド ドロップし、ダブルクリックまたは右クリックして、 **[編集]** をクリックし、次の **[Azure Blob Upload Task Editor (Azure BLOB アップロード タスク エディター)]** ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="930be-104">To add an **Azure Blob Upload Task**, drag-drop it to the SSIS Designer, and double-click or right-click and click **Edit** to see the following **Azure Blob Upload Task Editor** dialog box.</span></span>  
  
 <span data-ttu-id="930be-105">次の表で、このダイアログ ボックスの各フィールドを説明します。</span><span class="sxs-lookup"><span data-stu-id="930be-105">The following table provides descriptions for the fields in this dialog box.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="930be-106">**フィールド**</span><span class="sxs-lookup"><span data-stu-id="930be-106">**Field**</span></span>|<span data-ttu-id="930be-107">**説明**</span><span class="sxs-lookup"><span data-stu-id="930be-107">**Description**</span></span>|  
|<span data-ttu-id="930be-108">AzureStorageConnection</span><span class="sxs-lookup"><span data-stu-id="930be-108">AzureStorageConnection</span></span>|<span data-ttu-id="930be-109">既存の Azure ストレージ接続マネージャーを指定するか、Azure ストレージ アカウントを参照する新しい接続マネージャーを作成します。この接続マネージャーは、BLOB ファイルがホストされている場所をポイントします。</span><span class="sxs-lookup"><span data-stu-id="930be-109">Specify an existing Azure Storage Connection Manager or create a new one that refers to an Azure Storage Account, which points to where the blob files are hosted.</span></span>|  
|<span data-ttu-id="930be-110">BlobContainer</span><span class="sxs-lookup"><span data-stu-id="930be-110">BlobContainer</span></span>|<span data-ttu-id="930be-111">アップロードしたファイルを BLOB として保持する BLOB コンテナーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="930be-111">Specifies the name of the blob container that will hold the uploaded files as blobs.</span></span>|  
|<span data-ttu-id="930be-112">BlobDirectory</span><span class="sxs-lookup"><span data-stu-id="930be-112">BlobDirectory</span></span>|<span data-ttu-id="930be-113">アップロードしたファイルをブロック BLOB として格納する BLOB ディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="930be-113">Specifies the blob directory where the uploaded file will be stored as a block blob.</span></span> <span data-ttu-id="930be-114">BLOB ディレクトリは仮想階層構造です。</span><span class="sxs-lookup"><span data-stu-id="930be-114">The blob directory is a virtual hierarchical structure.</span></span> <span data-ttu-id="930be-115">BLOB が既に存在する場合は置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="930be-115">If the blob already exists, it will be replaced.</span></span>|  
|<span data-ttu-id="930be-116">LocalDirectory</span><span class="sxs-lookup"><span data-stu-id="930be-116">LocalDirectory</span></span>|<span data-ttu-id="930be-117">アップロードするファイルを含むローカル ディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="930be-117">Specify the local directory that contains the files to be uploaded.</span></span>|  
|<span data-ttu-id="930be-118">FileName</span><span class="sxs-lookup"><span data-stu-id="930be-118">FileName</span></span>|<span data-ttu-id="930be-119">指定された名前のパターンを使用したファイルを選択するための名前フィルターを指定します。</span><span class="sxs-lookup"><span data-stu-id="930be-119">Specifies a name filter to select files with the specified name pattern.</span></span> <span data-ttu-id="930be-120">例:</span><span class="sxs-lookup"><span data-stu-id="930be-120">E.g.</span></span> <span data-ttu-id="930be-121">MySheet\*.xls\* には、MySheet001.xls や MySheetABC.xlsx などのファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="930be-121">MySheet\*.xls\* includes files such as MySheet001.xls and MySheetABC.xlsx.</span></span>|  
|<span data-ttu-id="930be-122">TimeRangeFrom/TimeRangeTo</span><span class="sxs-lookup"><span data-stu-id="930be-122">TimeRangeFrom/TimeRangeTo</span></span>|<span data-ttu-id="930be-123">時間範囲フィルターを指定します。</span><span class="sxs-lookup"><span data-stu-id="930be-123">Specifies a time range filter.</span></span> <span data-ttu-id="930be-124">**TimeRangeFrom** から **TimeRangeTo** までの間に変更されたファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="930be-124">Files modified after **TimeRangeFrom** and before **TimeRangeTo** will be included.</span></span>|  
  
  

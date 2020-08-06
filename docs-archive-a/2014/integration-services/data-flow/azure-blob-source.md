---
title: Azure BLOB Source | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobsrc.f1
- sql11.dts.designer.afpblobsrc.f1
ms.assetid: 80645c5c-88c8-4fb0-8607-de1bb7bffcbb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5a14c7022437c8a23f898a0f29c211bd9ae82aa0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644588"
---
# <a name="azure-blob-source"></a><span data-ttu-id="e8bba-102">Azure BLOB Source</span><span class="sxs-lookup"><span data-stu-id="e8bba-102">Azure Blob Source</span></span>
 <span data-ttu-id="e8bba-103">**Azure BLOB Source** コンポーネントは、SSIS パッケージが Azure BLOB のデータを読み取ることを可能にします。</span><span class="sxs-lookup"><span data-stu-id="e8bba-103">The **Azure Blob Source** component enables an SSIS package to read data from an Azure blob.</span></span> <span data-ttu-id="e8bba-104">サポートされるファイル形式は、CSV および AVRO です。</span><span class="sxs-lookup"><span data-stu-id="e8bba-104">The supported file formats are: CSV and AVRO.</span></span> <span data-ttu-id="e8bba-105">Azure BLOB Source のエディターを表示するには、データ フロー デザイナー上に **Azure Blob Source** をドラッグ アンド ドロップし、これをダブルクリックしてエディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="e8bba-105">To see the editor for the Azure Blob Source, drag and drop **Azure Blob Source** on the data flow designer and double-click it to open the editor).</span></span>  
  
1.  <span data-ttu-id="e8bba-106">**[Azure storage connection manager]** (Azure Storage 接続マネージャー) フィールドに、既存の Azure Storage 接続マネージャーを指定するか、または Azure Storage アカウントを参照する新しい Azure Storage 接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="e8bba-106">For the **Azure storage connection manager** field, specify an existing Azure Storage Connection Manager or create a new one that refers to an Azure Storage Account.</span></span>  
  
2.  <span data-ttu-id="e8bba-107">**[Blob container name]** (BLOB コンテナー名) フィールドに、ソース ファイルを含む BLOB コンテナーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="e8bba-107">For the **Blob container name** field, specify the name of the blob container that contains source files.</span></span>  
  
3.  <span data-ttu-id="e8bba-108">**[Blob name]** (BLOB 名) フィールドに、BLOB のパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="e8bba-108">For the **Blob name** field, specify the path for the blob.</span></span>  
  
4.  <span data-ttu-id="e8bba-109">**[Blob file format]** (BLOB ファイル形式) フィールドに、使用する形式を指定します。</span><span class="sxs-lookup"><span data-stu-id="e8bba-109">For the **Blob file format** field, specify the blob format you want to use.</span></span>  
  
5.  <span data-ttu-id="e8bba-110">CSV 形式の場合は、 **[Column delimiter character]** (列区切り文字) に値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8bba-110">If the file format is CSV, you must specify the **Column delimiter character** value.</span></span> <span data-ttu-id="e8bba-111">さらに、ファイルの 1 行目に列名が含まれている場合は、 **[先頭データ行を列名として使用する]** も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8bba-111">Also select **Column names in the first data row** if the first row in the file contains column names.</span></span>  
  
6.  <span data-ttu-id="e8bba-112">接続情報を指定した後、 **[列]** ページで、SSIS データ フローのマップ元の列をマップ先の列にマップします。</span><span class="sxs-lookup"><span data-stu-id="e8bba-112">After specifying the connection information, switch to the **Columns** page to map source columns to destination columns for the SSIS data flow.</span></span>  
  
  

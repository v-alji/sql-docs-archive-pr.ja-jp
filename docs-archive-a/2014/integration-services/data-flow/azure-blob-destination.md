---
title: Azure Blob Destination | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobdest.f1
- sql11.dts.designer.afpblobdest.f1
ms.assetid: 820a1e7a-7182-4c7b-ab56-5b4097a7e042
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fb406d38b17748e8284acee4b2849a9fd99e53ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738556"
---
# <a name="azure-blob-destination"></a><span data-ttu-id="c84f9-102">Azure Blob Destination</span><span class="sxs-lookup"><span data-stu-id="c84f9-102">Azure Blob Destination</span></span>
  <span data-ttu-id="c84f9-103">**Azure Blob Destination** コンポーネントは、SSIS パッケージが Azure Blob にデータを書き込めるようにします。</span><span class="sxs-lookup"><span data-stu-id="c84f9-103">The **Azure Blob Destination** component enables an SSIS package to write data to an Azure blob.</span></span> <span data-ttu-id="c84f9-104">サポートされるファイル形式は、CSV および AVRO です。</span><span class="sxs-lookup"><span data-stu-id="c84f9-104">The supported file formats are: CSV and AVRO.</span></span> <span data-ttu-id="c84f9-105">**Azure Blob Destination**をデータフローデザイナーにドラッグアンドドロップし、ダブルクリックしてエディターを表示します。</span><span class="sxs-lookup"><span data-stu-id="c84f9-105">Ddrag-drop **Azure Blob Destination** to the data flow designer and double-click it to see the editor).</span></span>  
  
1.  <span data-ttu-id="c84f9-106">**[Azure storage connection manager]** (Azure Storage 接続マネージャー) フィールドに、既存の Azure Storage 接続マネージャーを指定するか、または Azure Storage アカウントを参照する新しい Azure Storage 接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="c84f9-106">For the **Azure storage connection manager** field, specify an existing Azure Storage Connection Manager or create a new one that refers to an Azure Storage Account.</span></span>  
  
2.  <span data-ttu-id="c84f9-107">**[Blob container name]** (BLOB コンテナー名) フィールドに、ソース ファイルを含む BLOB コンテナーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c84f9-107">For the **Blob container name** field, specify the name of the blob container that contains source files.</span></span>  
  
3.  <span data-ttu-id="c84f9-108">**[Blob name]** (BLOB 名) フィールドに、BLOB のパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="c84f9-108">For the **Blob name** field, specify the path for the blob.</span></span>  
  
4.  <span data-ttu-id="c84f9-109">**[Blob file format]** (BLOB ファイル形式) フィールドに、使用する形式を指定します。</span><span class="sxs-lookup"><span data-stu-id="c84f9-109">For the **Blob file format** field, specify the blob format you want to use.</span></span>  
  
5.  <span data-ttu-id="c84f9-110">CSV 形式の場合は、 **[Column delimiter character]** (列区切り文字) に値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c84f9-110">If the file format is CSV, you must specify the **Column delimiter character** value.</span></span> <span data-ttu-id="c84f9-111">また、ファイルの最初の行に列名が含まれている場合は、**最初のデータ行で列名**を選択します。</span><span class="sxs-lookup"><span data-stu-id="c84f9-111">Also  select **Column names in the first data row** if the first row in the file contains column names.</span></span>  
  
6.  <span data-ttu-id="c84f9-112">接続情報を指定した後、 **[列]** ページで、SSIS データ フローのマップ元の列をマップ先の列にマップします。</span><span class="sxs-lookup"><span data-stu-id="c84f9-112">After specifying the connection information, switch to the **Columns** page to map source columns to destination columns for the SSIS data flow.</span></span>  
  
  

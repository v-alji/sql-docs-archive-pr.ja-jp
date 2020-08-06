---
title: Azure Data Lake Store Source | Microsoft Docs
ms.custom: ''
ms.date: 06/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSSRC.F1
- SQL11.DTS.DESIGNER.AFPADLSSRC.F1
ms.assetid: 7d9e8457-62aa-4aea-98ee-7d1121dfae4f
author: yualan
ms.author: chugu
ms.openlocfilehash: e5bce25e303b055d734da6a00c73851f4eb0d7ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642255"
---
# <a name="azure-data-lake-store-source"></a><span data-ttu-id="97e47-102">Azure Data Lake Store Source</span><span class="sxs-lookup"><span data-stu-id="97e47-102">Azure Data Lake Store Source</span></span>
  <span data-ttu-id="97e47-103">**Azure Data Lake Store Source** コンポーネントは、SSIS パッケージが Azure Data Lake Store からデータを読み取れるようにします。</span><span class="sxs-lookup"><span data-stu-id="97e47-103">The **Azure Data Lake Store Source** component enables an SSIS package to read data from an Azure Data Lake Store.</span></span> <span data-ttu-id="97e47-104">サポートされるファイル形式は、テキストと Avro です。</span><span class="sxs-lookup"><span data-stu-id="97e47-104">The supported file formats are: Text and Avro.</span></span>
  
## <a name="configure-the-azure-data-lake-store-source"></a><span data-ttu-id="97e47-105">Azure Data Lake Store Source を構成する</span><span class="sxs-lookup"><span data-stu-id="97e47-105">Configure the Azure Data Lake Store Source</span></span> 
  
1.  <span data-ttu-id="97e47-106">Azure Data Lake Store のエディターを表示するには、データ フロー デザイナー上に **Azure Data Lake Store Source** をドラッグ アンド ドロップし、これをダブルクリックしてエディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="97e47-106">To see the editor for the Azure Data Lake Store Source, drag and drop **Azure Data Lake Store Source** on the data flow designer and double-click it to open the editor).</span></span>  
  
2.  <span data-ttu-id="97e47-107">**[Azure Data Lake Store connection manager (Azure Data Lake Store 接続マネージャー)]** フィールドに、既存の Azure Data Lake Store 接続マネージャーを指定するか、Azure Data Lake Store サービスを参照する新しいものを作成します。</span><span class="sxs-lookup"><span data-stu-id="97e47-107">For the **Azure Data Lake Store connection manager** field, specify an existing Azure Data Lake Store Connection Manager or create a new one that refers to an Azure Data Lake Store service.</span></span>  
  
    1.  <span data-ttu-id="97e47-108">**[ファイル パス]** フィールドには、Azure Data Lake Store のソース ファイルのファイル パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="97e47-108">For the **File Path** field, specify the file path of the source file in Azure Data Lake Store.</span></span>   
  
    2.  <span data-ttu-id="97e47-109">**[ファイル形式]** フィールドには、ソース ファイルのファイル形式を指定します。</span><span class="sxs-lookup"><span data-stu-id="97e47-109">For the **File format** field, specify the file format of the source file.</span></span>  
  
        <span data-ttu-id="97e47-110">テキスト ファイル形式の場合は、 **[列の区切り文字]** に値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97e47-110">If the file format is Text, you must specify the **Column delimiter character** value.</span></span> <span data-ttu-id="97e47-111">さらに、ファイルの 1 行目に列名が含まれている場合は、 **[先頭データ行を列名として使用する]** も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97e47-111">Also select **Column names in the first data row** if the first row in the file contains column names.</span></span>  
  
3.  <span data-ttu-id="97e47-112">接続情報を指定した後、 **[列]** ページで、SSIS データ フローのマップ元の列をマップ先の列にマップします。</span><span class="sxs-lookup"><span data-stu-id="97e47-112">After specifying the connection information, switch to the **Columns** page to map source columns to destination columns for the SSIS data flow.</span></span>  

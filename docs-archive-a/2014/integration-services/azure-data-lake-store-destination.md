---
title: Azure Data Lake Store Destination | Microsoft Docs
ms.custom: ''
ms.date: 06/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSDEST.F1
- SQL11.DTS.DESIGNER.AFPADLSDEST.F1
ms.assetid: d0e86032-2a6b-48b2-898f-e94328474fde
author: yualan
ms.author: chugu
ms.openlocfilehash: 14248d14b6a944250c33a19c8cf83ab0e0330587
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740230"
---
# <a name="azure-data-lake-store-destination"></a><span data-ttu-id="7fffa-102">Azure Data Lake Store Destination</span><span class="sxs-lookup"><span data-stu-id="7fffa-102">Azure Data Lake Store Destination</span></span>
  <span data-ttu-id="7fffa-103">**Azure Data Lake Store Destination** コンポーネントは、SSIS パッケージが Azure Data Lake Store にデータを書き込めるようにします。</span><span class="sxs-lookup"><span data-stu-id="7fffa-103">The **Azure Data Lake Store Destination** component enables an SSIS package to write data to an Azure Data Lake Store.</span></span> <span data-ttu-id="7fffa-104">サポートされるファイル形式は、テキスト、Avro、および ORC です。</span><span class="sxs-lookup"><span data-stu-id="7fffa-104">The supported file formats are: Text, Avro and ORC.</span></span> 
  
## <a name="configure-the-azure-data-lake-store-destination"></a><span data-ttu-id="7fffa-105">Azure Data Lake Store Destination を構成する</span><span class="sxs-lookup"><span data-stu-id="7fffa-105">Configure the Azure Data Lake Store Destination</span></span> 

1. <span data-ttu-id="7fffa-106">**Azure Data Lake Store Destination** をデータ フロー デザイナーにドラッグ アンド ドロップし、ダブルクリックしてエディターを表示します。</span><span class="sxs-lookup"><span data-stu-id="7fffa-106">Drag-drop **Azure Data Lake Store Destination** to the data flow designer and double-click it to see the editor.</span></span>  

2.  <span data-ttu-id="7fffa-107">**[Azure Data Lake Store connection manager (Azure Data Lake Store 接続マネージャー)]** フィールドに、既存の Azure Data Lake Store 接続マネージャーを指定するか、Azure Data Lake Store サービスを参照する新しいものを作成します。</span><span class="sxs-lookup"><span data-stu-id="7fffa-107">For the **Azure Data Lake Store connection manager** field, specify an existing Azure Data Lake Store Connection Manager or create a new one that refers to an Azure Data Lake Store service.</span></span>  
  
    1.  <span data-ttu-id="7fffa-108">**[ファイル パス]** フィールドには、データを書き込むファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="7fffa-108">For the **File Path** field, specify the file name you want to write data to.</span></span> <span data-ttu-id="7fffa-109">このファイルが既に存在する場合、その内容は上書きされます。</span><span class="sxs-lookup"><span data-stu-id="7fffa-109">If this file already exist, its content will be overwritten.</span></span>  
  
    2.  <span data-ttu-id="7fffa-110">**[ファイル形式]** フィールドには、使用するファイル形式を指定します。</span><span class="sxs-lookup"><span data-stu-id="7fffa-110">For the **File format** field, specify the file format you want to use.</span></span>  
  
        <span data-ttu-id="7fffa-111">テキスト ファイル形式の場合は、 **[列の区切り文字]** に値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7fffa-111">If the file format is Text, you must specify the **Column delimiter character** value.</span></span> <span data-ttu-id="7fffa-112">また、ファイルの最初の行に列名が含まれている場合は、**最初のデータ行で列名**を選択します。</span><span class="sxs-lookup"><span data-stu-id="7fffa-112">Also  select **Column names in the first data row** if the first row in the file contains column names.</span></span>  

        <span data-ttu-id="7fffa-113">ORC ファイル形式の場合は、対応するプラットフォームの JRE をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7fffa-113">If the file format is ORC, you need to install JRE of corresponding platform.</span></span> 
  
3.  <span data-ttu-id="7fffa-114">接続情報を指定した後、 **[列]** ページで、SSIS データ フローのマップ元の列をマップ先の列にマップします。</span><span class="sxs-lookup"><span data-stu-id="7fffa-114">After specifying the connection information, switch to the **Columns** page to map source columns to destination columns for the SSIS data flow.</span></span>  

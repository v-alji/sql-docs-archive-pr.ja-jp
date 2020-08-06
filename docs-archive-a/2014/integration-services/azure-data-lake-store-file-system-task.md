---
title: Azure Data Lake Store ファイル システム タスク | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSTASK.F1
- SQL11.DTS.DESIGNER.AFPADLSTASK.F1
ms.assetid: 02b9edd7-6ef9-463e-abbf-e1830bcae875
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1bc37e774c5346190635e50259deb47f2f22a054
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642259"
---
# <a name="azure-data-lake-store-file-system-task"></a><span data-ttu-id="53e8e-102">Azure Data Lake Store ファイル システム タスク</span><span class="sxs-lookup"><span data-stu-id="53e8e-102">Azure Data Lake Store File System Task</span></span>

<span data-ttu-id="53e8e-103">**Azure Data Lake Store ファイルシステムタスク**を使用すると、ユーザーは[Azure Data Lake Store (adls)](https://azure.microsoft.com/services/data-lake-store/)に対してさまざまなファイルシステム操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="53e8e-103">The **Azure Data Lake Store File System Task** enables users to perform various file system operations on [Azure Data Lake Store (ADLS)](https://azure.microsoft.com/services/data-lake-store/).</span></span>

<span data-ttu-id="53e8e-104">パッケージに Azure Data Lake Store ファイル システム タスクを追加するには、SSIS ツールボックスからデザイナー キャンバスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="53e8e-104">To add an Azure Data Lake Store File System Task to a package, drag it from SSIS Toolbox to the designer canvas.</span></span> <span data-ttu-id="53e8e-105">次に、タスクをダブルクリックするか、タスクを右クリックして [**編集**] を選択し、[タスクエディター] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="53e8e-105">Then double-click the task, or right-click the task and select **Edit**, to open the task editor dialog box.</span></span>

<span data-ttu-id="53e8e-106">**[操作]** プロパティでは、実行するファイル システム操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="53e8e-106">The **Operation** property specifies the file system operation to perform.</span></span> <span data-ttu-id="53e8e-107">次の操作がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="53e8e-107">The following operations are supported.</span></span>

* <span data-ttu-id="53e8e-108">**CopyToADLS:** ADLS にファイルをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="53e8e-108">**CopyToADLS:** Upload files to ADLS.</span></span>
* <span data-ttu-id="53e8e-109">**CopyFromADLS:** ADLS からファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="53e8e-109">**CopyFromADLS:** Download files from ADLS.</span></span>

<span data-ttu-id="53e8e-110">操作に対して、Azure Data Lake 接続マネージャーを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="53e8e-110">For any operation, you have to specify an Azure Data Lake connection manager.</span></span>

<span data-ttu-id="53e8e-111">各操作に固有のプロパティの説明を次に示します。</span><span class="sxs-lookup"><span data-stu-id="53e8e-111">Here are the descriptions of the properties specific to each operation.</span></span>

## <a name="copytoadls"></a><span data-ttu-id="53e8e-112">CopyToADLS</span><span class="sxs-lookup"><span data-stu-id="53e8e-112">CopyToADLS</span></span>

* <span data-ttu-id="53e8e-113">**Localdirectory:** アップロードするファイルが格納されているソースディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="53e8e-113">**LocalDirectory:** Specifies the source directory which contains files to upload.</span></span>
* <span data-ttu-id="53e8e-114">**FileNamePattern:** ソース ファイルのファイル名フィルターを指定します。</span><span class="sxs-lookup"><span data-stu-id="53e8e-114">**FileNamePattern:** Specifies a file name filter for source files.</span></span> <span data-ttu-id="53e8e-115">名前が指定したパターンに一致するファイルのみがアップロードされます。</span><span class="sxs-lookup"><span data-stu-id="53e8e-115">Only files whose name matches the specified pattern will be uploaded.</span></span> <span data-ttu-id="53e8e-116">ワイルドカードの `*` と `?` がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="53e8e-116">Wildcards `*` and `?` are supported.</span></span>
* <span data-ttu-id="53e8e-117">**SearchRecursively:** アップロードするファイルのソース ディレクトリ内で再帰的に検索するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="53e8e-117">**SearchRecursively:** Specifies whether to search recursively within the source directory for files to upload.</span></span>
* <span data-ttu-id="53e8e-118">**AzureDataLakeDirectory:** ファイルのアップロード先となる ADLS ディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="53e8e-118">**AzureDataLakeDirectory:** Specifies the ADLS destination directory to upload files to.</span></span>
* <span data-ttu-id="53e8e-119">**Fileexpiry 切れ:** ADLS にアップロードされたファイルの有効期限の日付と時刻を指定します。または、ファイルが期限切れにならないことを示すために、このプロパティを空白のままにします。</span><span class="sxs-lookup"><span data-stu-id="53e8e-119">**FileExpiry:** Specifies an expiration date and time for the files uploaded to ADLS, or leave this property blank to indicate that the files never expire.</span></span>

## <a name="copyfromadls"></a><span data-ttu-id="53e8e-120">CopyFromADLS</span><span class="sxs-lookup"><span data-stu-id="53e8e-120">CopyFromADLS</span></span>

* <span data-ttu-id="53e8e-121">**AzureDataLakeDirectory:** ダウンロードするファイルを含む ADLS ソース ディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="53e8e-121">**AzureDataLakeDirectory:** Specifies the ADLS source directory which contains the files to download.</span></span>
* <span data-ttu-id="53e8e-122">**SearchRecursively:** ダウンロードするファイルのソース ディレクトリ内で再帰的に検索するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="53e8e-122">**SearchRecursively:** Specifies whether to search recursively within the source directory for files to download.</span></span>
* <span data-ttu-id="53e8e-123">**LocalDirectory:** ダウンロードしたファイルの格納先となるディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="53e8e-123">**LocalDirectory:** Specifies the destination directory to store downloaded files.</span></span>

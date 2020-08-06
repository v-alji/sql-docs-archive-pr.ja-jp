---
title: ADO NET 変換先 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetdest.f1
helpviewer_keywords:
- destinations [Integration Services], ADO.NET
- ADO.NET destination
ms.assetid: cb883990-d875-4d8b-b868-45f9f15ebeae
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8289a8c91c7b78749a341cc95055562d01164866
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716554"
---
# <a name="ado-net-destination"></a><span data-ttu-id="43888-102">ADO NET 変換先</span><span class="sxs-lookup"><span data-stu-id="43888-102">ADO NET Destination</span></span>
  <span data-ttu-id="43888-103">ADO NET 変換先では、データベースのテーブルやビューを使用する、さまざまな [!INCLUDE[vstecado](../../includes/vstecado-md.md)]互換データベースにデータを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="43888-103">The ADO NET destination loads data into a variety of [!INCLUDE[vstecado](../../includes/vstecado-md.md)]-compliant databases that use a database table or view.</span></span> <span data-ttu-id="43888-104">このデータを既存のテーブルやビューに読み込むことができますが、新しいテーブルを作成して、そこにデータを読み込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="43888-104">You have the option of loading this data into an existing table or view, or you can create a new table and load the data into the new table.</span></span>  
  
 <span data-ttu-id="43888-105">ADO NET 変換先を使用して [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] に接続できます。</span><span class="sxs-lookup"><span data-stu-id="43888-105">You can use the ADO NET destination to connect to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].</span></span> <span data-ttu-id="43888-106">OLE DB を使用した [!INCLUDE[ssSDS](../../includes/sssds-md.md)] への接続はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="43888-106">Connecting to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] by using OLE DB is not supported.</span></span> <span data-ttu-id="43888-107">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] の詳細については、「[一般的な制限事項とガイドライン (Azure SQL Database)](https://go.microsoft.com/fwlink/?LinkId=248228)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43888-107">For more information about [!INCLUDE[ssSDS](../../includes/sssds-md.md)], see [General Guidelines and Limitations (Azure SQL Database)](https://go.microsoft.com/fwlink/?LinkId=248228).</span></span>  
  
## <a name="troubleshooting-the-ado-net-destination"></a><span data-ttu-id="43888-108">ADO NET 変換先のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="43888-108">Troubleshooting the ADO NET Destination</span></span>  
 <span data-ttu-id="43888-109">ADO NET 変換先による外部データ プロバイダーの呼び出しをログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="43888-109">You can log the calls that the ADO NET destination makes to external data providers.</span></span> <span data-ttu-id="43888-110">このログ機能を使用すると、ADO NET 変換先による外部データ ソースへのデータ保存に関するトラブルシューティングを行えます。</span><span class="sxs-lookup"><span data-stu-id="43888-110">You can use this logging capability to troubleshoot the saving of data to external data sources that the ADO NET destination performs.</span></span> <span data-ttu-id="43888-111">ADO NET 変換先による外部データ プロバイダーの呼び出しのログを記録するには、パッケージ ログ記録を有効にして、パッケージ レベルで **Diagnostic** イベントを選択します。</span><span class="sxs-lookup"><span data-stu-id="43888-111">To log the calls that the ADO NET destination makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="43888-112">詳細については、「 [パッケージ実行のトラブルシューティング ツール](../troubleshooting/troubleshooting-tools-for-package-execution.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43888-112">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
## <a name="configuring-the-ado-net-destination"></a><span data-ttu-id="43888-113">ADO NET 変換先の構成</span><span class="sxs-lookup"><span data-stu-id="43888-113">Configuring the ADO NET Destination</span></span>  
 <span data-ttu-id="43888-114">この変換先は [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーを使用してデータ ソースに接続します。また、この接続マネージャーでは、使用する [!INCLUDE[vstecado](../../includes/vstecado-md.md)] プロバイダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="43888-114">This destination uses an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to connect to a data source and the connection manager specifies the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] provider to use.</span></span> <span data-ttu-id="43888-115">詳細については、「 [ADO.NET Connection Manager](../connection-manager/ado-net-connection-manager.md)」(ADO.NET 接続マネージャー) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43888-115">For more information, see [ADO.NET Connection Manager](../connection-manager/ado-net-connection-manager.md).</span></span>  
  
 <span data-ttu-id="43888-116">ADO NET 変換先には、入力列と変換先データ ソースの列との間のマッピングが含まれています。</span><span class="sxs-lookup"><span data-stu-id="43888-116">An ADO NET destination includes mappings between input columns and columns in the destination data source.</span></span> <span data-ttu-id="43888-117">入力列を変換先のすべての列にマップする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="43888-117">You do not have to map input columns to all destination columns.</span></span> <span data-ttu-id="43888-118">ただし、一部の変換先列のプロパティで、入力列のマップが必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="43888-118">However, the properties of some destination columns can require the mapping of input columns.</span></span> <span data-ttu-id="43888-119">マップしない場合、エラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="43888-119">Otherwise, errors might occur.</span></span> <span data-ttu-id="43888-120">たとえば、変換先列で NULL 値が許容されていない場合は、入力列をその変換先列にマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="43888-120">For example, if a destination column does not allow for null values, you must map an input column to that destination column.</span></span> <span data-ttu-id="43888-121">また、マップされる列のデータ型には互換性がある必要があります。</span><span class="sxs-lookup"><span data-stu-id="43888-121">In addition, the data types of mapped columns must be compatible.</span></span> <span data-ttu-id="43888-122">たとえば、 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] プロバイダーで文字列データ型の入力列を数値データ型の変換先列にマップすることがサポートされていなければ、その操作はできません。</span><span class="sxs-lookup"><span data-stu-id="43888-122">For example, you cannot map an input column with a string data type to a destination column with a numeric data type if the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] provider does not support this mapping.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="43888-123">では、データ型が IMAGE 型に設定された列にテキストを挿入することはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="43888-123">does not support inserting text into columns whose data type is set to image.</span></span> <span data-ttu-id="43888-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ型の詳細については、「[データ型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43888-124">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="43888-125">ADO NET 変換先では、DT_DBTIME 型に設定されている入力列を datetime 型に設定されているデータベース列にマップすることがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="43888-125">The ADO NET destination does not support mapping an input column whose type is set to DT_DBTIME to a database column whose type is set to datetime.</span></span> <span data-ttu-id="43888-126">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のデータ型について詳しくは、「 [Integration Services のデータ型](integration-services-data-types.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="43888-126">For more information about [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types, see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="43888-127">ADO NET 変換先は、1 つの標準入力と 1 つのエラー出力をとります。</span><span class="sxs-lookup"><span data-stu-id="43888-127">The ADO NET destination has one regular input and one error output.</span></span>  
  
 <span data-ttu-id="43888-128">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="43888-128">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="43888-129">**[ADO NET 変換先エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="43888-129">For more information about the properties that you can set in the **ADO NET Destination Editor** dialog box, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="43888-130">[[ADO NET 変換先エディター] ([接続マネージャー] ページ)](../ado-net-destination-editor-connection-manager-page.md)</span><span class="sxs-lookup"><span data-stu-id="43888-130">[ADO NET Destination Editor &#40;Connection Manager Page&#41;](../ado-net-destination-editor-connection-manager-page.md)</span></span>  
  
-   <span data-ttu-id="43888-131">[[ADO NET 変換先エディター] &#40;[マッピング] ページ&#41;](../ado-net-destination-editor-mappings-page.md)</span><span class="sxs-lookup"><span data-stu-id="43888-131">[ADO NET Destination Editor &#40;Mappings Page&#41;](../ado-net-destination-editor-mappings-page.md)</span></span>  
  
-   <span data-ttu-id="43888-132">[[ADO NET 変換先エディター] &#40;[エラー出力] ページ&#41;](../ado-net-destination-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="43888-132">[ADO NET Destination Editor &#40;Error Output Page&#41;](../ado-net-destination-editor-error-output-page.md)</span></span>  
  
 <span data-ttu-id="43888-133">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="43888-133">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="43888-134">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="43888-134">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="43888-135">Common Properties</span><span class="sxs-lookup"><span data-stu-id="43888-135">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="43888-136">ADO NET カスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="43888-136">ADO NET Custom Properties</span></span>](ado-net-custom-properties.md)  
  
 <span data-ttu-id="43888-137">プロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](set-the-properties-of-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43888-137">For more information about how to set properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  

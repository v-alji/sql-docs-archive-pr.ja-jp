---
title: ADO NET ソース | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetsource.f1
helpviewer_keywords:
- ADO.NET source
- sources [Integration Services], ADO.NET
- sources [Integration Services], DataReader
- .NET Framework [Integration Services]
- DataReader source
ms.assetid: 2a2f1750-2cda-4dda-9dca-623a96a6b3c0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: eb50a6171ed29fc5328663d8ce9992e0462e02f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738563"
---
# <a name="ado-net-source"></a><span data-ttu-id="8ba16-102">ADO NET ソース</span><span class="sxs-lookup"><span data-stu-id="8ba16-102">ADO NET Source</span></span>
  <span data-ttu-id="8ba16-103">ADO NET ソースは .NET プロバイダーのデータを呼び出し、そのデータをデータ フローで使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="8ba16-103">The ADO NET source consumes data from a .NET provider and makes the data available to the data flow.</span></span>  
  
 <span data-ttu-id="8ba16-104">ADO NET ソースを使用して [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] に接続できます。</span><span class="sxs-lookup"><span data-stu-id="8ba16-104">You can use the ADO NET source to connect to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].</span></span> <span data-ttu-id="8ba16-105">OLE DB を使用した [!INCLUDE[ssSDS](../../includes/sssds-md.md)] への接続はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="8ba16-105">Connecting to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] by using OLE DB is not supported.</span></span> <span data-ttu-id="8ba16-106">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] の詳細については、「[一般的な制限事項とガイドライン (Azure SQL Database)](https://go.microsoft.com/fwlink/?LinkId=248228)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ba16-106">For more information about [!INCLUDE[ssSDS](../../includes/sssds-md.md)], see [General Guidelines and Limitations (Azure SQL Database)](https://go.microsoft.com/fwlink/?LinkId=248228).</span></span>  
  
## <a name="data-type-support"></a><span data-ttu-id="8ba16-107">データ型のサポート</span><span class="sxs-lookup"><span data-stu-id="8ba16-107">Data Type Support</span></span>  
 <span data-ttu-id="8ba16-108">ソースは、特定の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] データ型にマップされないデータ型を DT_NTEXT [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] データ型に変換します。</span><span class="sxs-lookup"><span data-stu-id="8ba16-108">The source converts any data type that does not map to a specific [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type to the DT_NTEXT [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type.</span></span> <span data-ttu-id="8ba16-109">この変換はデータ型が `System.Object` である場合でも行われます。</span><span class="sxs-lookup"><span data-stu-id="8ba16-109">This conversion occurs even if the data type is `System.Object`.</span></span>  
  
 <span data-ttu-id="8ba16-110">DT_NTEXT データ型から DT_WSTR データ型に、または DT_WSTR データ型から DT_NTEXT データ型に変更できます。</span><span class="sxs-lookup"><span data-stu-id="8ba16-110">You can change the DT_NTEXT data type to the DT_WSTR data type, or the change DT_WSTR to DT_NTEXT.</span></span> <span data-ttu-id="8ba16-111">データ型を変更するには、ADO NET ソースの **[詳細エディター]** ダイアログ ボックスで **DataType** プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="8ba16-111">You change data types by setting the **DataType** property in the **Advanced Editor** dialog box of the ADO NET source.</span></span> <span data-ttu-id="8ba16-112">詳細については、「 [Common Properties](../common-properties.md)」(共通プロパティ) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ba16-112">For more information, see [Common Properties](../common-properties.md).</span></span>  
  
 <span data-ttu-id="8ba16-113">ADO NET ソースの後にデータ変換の変換を使用することによって、DT_NTEXT データ型を DT_BYTES データ型または DT_STR データ型に変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="8ba16-113">The DT_NTEXT data type can also be converted to the DT_BYTES or DT_STR data type by using a Data Conversion transformation after the ADO NET source.</span></span> <span data-ttu-id="8ba16-114">詳細については、「 [Data Conversion Transformation](transformations/data-conversion-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ba16-114">For more information, see [Data Conversion Transformation](transformations/data-conversion-transformation.md).</span></span>  
  
 <span data-ttu-id="8ba16-115">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]では、日付データ型 DT_DBDATE、DT_DBTIME2、DT_DBTIMESTAMP2、および DT_DBTIMESTAMPOFFSET は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の特定の日付データ型にマップされます。</span><span class="sxs-lookup"><span data-stu-id="8ba16-115">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], the date data types, DT_DBDATE, DT_DBTIME2, DT_DBTIMESTAMP2, and DT_DBTIMESTAMPOFFSET, map to certain date data types in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8ba16-116">ADO NET ソースを構成して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が使用する日付データ型を [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] が使用する日付データ型に変換できます。</span><span class="sxs-lookup"><span data-stu-id="8ba16-116">You can configure the ADO NET source to convert the date data types from those that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses to those that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] uses.</span></span> <span data-ttu-id="8ba16-117">このような日付データ型を変換する ADO NET ソースを構成するには、 **接続マネージャーの** Type System Version [!INCLUDE[vstecado](../../includes/vstecado-md.md)] プロパティを **[最新]** に設定します</span><span class="sxs-lookup"><span data-stu-id="8ba16-117">To configure the ADO NET source to convert these date data types, set the **Type System Version** property of the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to **Latest**.</span></span> <span data-ttu-id="8ba16-118">( **Type System Version** プロパティは、 **[接続マネージャー]** ダイアログ ボックスの **[すべて]** ページにあります。</span><span class="sxs-lookup"><span data-stu-id="8ba16-118">(The **Type System Version** property is on the **All** page of the **Connection Manager** dialog box.</span></span> <span data-ttu-id="8ba16-119">**[接続マネージャー]** ダイアログ ボックスを開くには、 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーを右クリックし、 **[編集]** をクリックします)。</span><span class="sxs-lookup"><span data-stu-id="8ba16-119">To open the **Connection Manager** dialog box, right-click the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager, and then click **Edit**.)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8ba16-120">**接続マネージャーの** Type System Version [!INCLUDE[vstecado](../../includes/vstecado-md.md)] プロパティが **[SQL Server 2005]** に設定されていると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日付データ型は DT_WSTR に変換されます。</span><span class="sxs-lookup"><span data-stu-id="8ba16-120">If the **Type System Version** property for the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager is set to **SQL Server 2005**, the system converts the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date data types to DT_WSTR.</span></span>  
  
 <span data-ttu-id="8ba16-121">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 接続マネージャーで、プロバイダーを .NET Data Provider for [!INCLUDE[vstecado](../../includes/vstecado-md.md)] (SqlClient) と指定すると、システムはユーザー定義データ型 (UDT) は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バイナリ ラージ オブジェクト (BLOB) に変換されます。</span><span class="sxs-lookup"><span data-stu-id="8ba16-121">The system converts user-defined data types (UDTs) to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] binary large objects (BLOB) when the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager specifies the provider as the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient).</span></span> <span data-ttu-id="8ba16-122">UDT データ型の変換時には、次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="8ba16-122">The system applies the following rules when it converts the UDT data type:</span></span>  
  
-   <span data-ttu-id="8ba16-123">データが大きくない UDT の場合、データは DT_BYTES に変換されます。</span><span class="sxs-lookup"><span data-stu-id="8ba16-123">If the data is a non-large UDT, the system converts the data to DT_BYTES.</span></span>  
  
-   <span data-ttu-id="8ba16-124">データが大きくない UDT の場合、データベースの列の **[長さ]** プロパティは -1 または 8,000 バイトより大きい値に設定され、データは DT_IMAGE に変換されます。</span><span class="sxs-lookup"><span data-stu-id="8ba16-124">If the data is a non-large UDT, and the **Length** property of the column on the database is set to -1 or a value greater than 8,000 bytes, the system converts the data to DT_IMAGE.</span></span>  
  
-   <span data-ttu-id="8ba16-125">データが大きい UDT の場合、データは DT_IMAGE に変換されます。</span><span class="sxs-lookup"><span data-stu-id="8ba16-125">If the data is a large UDT, the system converts the data to DT_IMAGE.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8ba16-126">ADO NET ソースがエラー出力を使用するように構成されていない場合、データは DT_IMAGE 列に 8,000 バイトのチャンク単位でストリームされます。</span><span class="sxs-lookup"><span data-stu-id="8ba16-126">If the ADO NET source is not configured to use error output, the system streams the data to the DT_IMAGE column in chunks of 8,000 bytes.</span></span> <span data-ttu-id="8ba16-127">ADO NET ソースがエラー出力を使用するように構成されている場合、バイトの配列全体が DT_IMAGE 列に渡されます。</span><span class="sxs-lookup"><span data-stu-id="8ba16-127">If the ADO NET source is configured to use error output, the system passes the whole array of bytes to the DT_IMAGE column.</span></span> <span data-ttu-id="8ba16-128">エラー出力を使用するコンポーネントを構成する方法の詳細については、「 [Error Handling in Data](error-handling-in-data.md)」(データのエラー処理) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ba16-128">For more information about how to configure components to use error output, see [Error Handling in Data](error-handling-in-data.md).</span></span>  
  
 <span data-ttu-id="8ba16-129">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] データ型、サポートされるデータ型変換、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を含む特定のデータベース間でのデータ型マッピングの詳細については、「 [Integration Services のデータ型](integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ba16-129">For more information about the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types, supported data type conversions, and data type mapping across certain databases including [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="8ba16-130">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] データ型をマネージド データ型にマッピングする方法については、「[データ フロー内のデータ型の処理](../extending-packages-custom-objects/data-flow/working-with-data-types-in-the-data-flow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ba16-130">For information about mapping [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types to managed data types, see [Working with Data Types in the Data Flow](../extending-packages-custom-objects/data-flow/working-with-data-types-in-the-data-flow.md).</span></span>  
  
## <a name="ado-net-source-troubleshooting"></a><span data-ttu-id="8ba16-131">ADO NET ソースのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="8ba16-131">ADO NET Source Troubleshooting</span></span>  
 <span data-ttu-id="8ba16-132">ADO NET ソースによる外部データ プロバイダーの呼び出しをログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="8ba16-132">You can log the calls that the ADO NET source makes to external data providers.</span></span> <span data-ttu-id="8ba16-133">このログ機能を使用すると、ADO NET ソースによる外部データ ソースからのデータ読み込みに関するトラブルシューティングを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="8ba16-133">You can use this logging capability to troubleshoot the loading of data from external data sources that the ADO NET source performs.</span></span> <span data-ttu-id="8ba16-134">ADO NET ソースによる外部データ プロバイダーの呼び出しのログを記録するには、パッケージ ログ記録を有効にして、パッケージ レベルで **Diagnostic** イベントを選択します。</span><span class="sxs-lookup"><span data-stu-id="8ba16-134">To log the calls that the ADO NET source makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="8ba16-135">詳細については、「 [パッケージ実行のトラブルシューティング ツール](../troubleshooting/troubleshooting-tools-for-package-execution.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ba16-135">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
## <a name="ado-net-source-configuration"></a><span data-ttu-id="8ba16-136">ADO NET ソースの構成</span><span class="sxs-lookup"><span data-stu-id="8ba16-136">ADO NET Source Configuration</span></span>  
 <span data-ttu-id="8ba16-137">ADO NET ソースを構成するには、結果セットを定義する SQL ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="8ba16-137">You configure the ADO NET source by providing the SQL statement that defines the result set.</span></span> <span data-ttu-id="8ba16-138">たとえば、 [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] データベースに接続し、SQL ステートメント `SELECT * FROM Production.Product` を使用する ADO NET ソースは、 **Production.Product** テーブルのすべての行を抽出し、データセットを下流コンポーネントに提供します。</span><span class="sxs-lookup"><span data-stu-id="8ba16-138">For example, an ADO NET source that connects to the [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] database and uses the SQL statement `SELECT * FROM Production.Product` extracts all the rows from the **Production.Product** table and provides the dataset to a downstream component.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8ba16-139">SQL ステートメントを使用して、一時テーブルから結果を返すストアド プロシージャが呼び出す場合は、WITH RESULT SETS オプションを使用して結果セットのメタデータを定義します。</span><span class="sxs-lookup"><span data-stu-id="8ba16-139">When you use an SQL statement to invoke a stored procedure that returns results from a temporary table, use the WITH RESULT SETS option to define metadata for the result set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8ba16-140">SQL ステートメントを使用してストアド プロシージャを実行する際に、パッケージが次のエラーで失敗した場合は、EXEC ステートメントの前に `SET FMTONLY OFF` ステートメントを追加すると、エラーを解決できることがあります。</span><span class="sxs-lookup"><span data-stu-id="8ba16-140">If you use an SQL statement to execute a stored procedure and the package fails with the following error, you may be able to resolve the error by adding the `SET FMTONLY OFF` statement before the exec statement.</span></span>  
>   
>  <span data-ttu-id="8ba16-141">**列 <column_name> がデータ ソースに見つかりません。**</span><span class="sxs-lookup"><span data-stu-id="8ba16-141">**Column <column_name> cannot be found at the datasource.**</span></span>  
  
 <span data-ttu-id="8ba16-142">ADO NET ソースは [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーを使用してデータ ソースに接続します。この接続マネージャーは .NET プロバイダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="8ba16-142">The ADO NET source uses an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to connect to a data source, and the connection manager specifies the .NET provider.</span></span> <span data-ttu-id="8ba16-143">詳細については、「 [ADO.NET Connection Manager](../connection-manager/ado-net-connection-manager.md)」(ADO.NET 接続マネージャー) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ba16-143">For more information, see [ADO.NET Connection Manager](../connection-manager/ado-net-connection-manager.md).</span></span>  
  
 <span data-ttu-id="8ba16-144">ADO NET ソースは、1 つの標準出力と 1 つのエラー出力をとります。</span><span class="sxs-lookup"><span data-stu-id="8ba16-144">The ADO NET source has one regular output and one error output.</span></span>  
  
 <span data-ttu-id="8ba16-145">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="8ba16-145">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="8ba16-146">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ba16-146">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="8ba16-147">Common Properties</span><span class="sxs-lookup"><span data-stu-id="8ba16-147">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="8ba16-148">ADO NET カスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="8ba16-148">ADO NET Custom Properties</span></span>](ado-net-custom-properties.md)  
  
 <span data-ttu-id="8ba16-149">プロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](set-the-properties-of-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ba16-149">For more information about how to set properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ba16-150">参照</span><span class="sxs-lookup"><span data-stu-id="8ba16-150">See Also</span></span>  
 <span data-ttu-id="8ba16-151">[DataReader 変換先](datareader-destination.md) </span><span class="sxs-lookup"><span data-stu-id="8ba16-151">[DataReader Destination](datareader-destination.md) </span></span>  
 <span data-ttu-id="8ba16-152">[ADO NET 変換先](ado-net-destination.md) </span><span class="sxs-lookup"><span data-stu-id="8ba16-152">[ADO NET Destination](ado-net-destination.md) </span></span>  
 [<span data-ttu-id="8ba16-153">データ フロー</span><span class="sxs-lookup"><span data-stu-id="8ba16-153">Data Flow</span></span>](data-flow.md)  
  
  

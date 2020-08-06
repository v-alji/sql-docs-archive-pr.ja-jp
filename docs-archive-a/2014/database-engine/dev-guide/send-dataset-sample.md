---
title: データセットの送信サンプル |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: d10dacbc-1b0f-4a4b-b53b-83eae2a6d809
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: de50007641dd39dc7aa2bcb16ea8da9fde4cabb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645824"
---
# <a name="send-dataset-sample"></a><span data-ttu-id="b86c1-102">Send DataSet サンプル</span><span class="sxs-lookup"><span data-stu-id="b86c1-102">Send DataSet Sample</span></span>
  <span data-ttu-id="b86c1-103">Send `DataSet` サンプルでは、サーバー側の共通言語ランタイム (CLR) ベースのストアド プロシージャ内で、クライアントへの結果セットとして ADO.NET ベースの `DataSet` を返す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b86c1-103">The Send `DataSet` sample demonstrates how to return an ADO.NET based `DataSet` within a server side common language runtime (CLR)-based stored procedure as a result set to the client.</span></span> <span data-ttu-id="b86c1-104">この方法は、このようなストアド プロシージャがクエリの結果を使用して `DataSet` にデータを格納し、その `DataSet` に含まれているデータを操作する場合などに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b86c1-104">This is useful, for example, when such a stored procedure fills a `DataSet` using the results of a query, and then manipulates the data that is contained in that `DataSet`.</span></span> <span data-ttu-id="b86c1-105">また、ストアド プロシージャによって `DataSet` を新しく作成してデータを設定する場合にも役立ちます。このサンプルは、`DataSetUtilities` および `TestSendDataSet` という 2 つのクラスで構成されています。</span><span class="sxs-lookup"><span data-stu-id="b86c1-105">Alternatively this is useful if the stored procedure creates and populates a `DataSet` from scratch.The sample is composed of two classes, `DataSetUtilities` and `TestSendDataSet`.</span></span> <span data-ttu-id="b86c1-106">`SendDataSet` クラスの `DataSetUtilities` メソッドには、`DataSet` インスタンスのコンテンツをクライアントに送信するための汎用的な手段が実装されています。</span><span class="sxs-lookup"><span data-stu-id="b86c1-106">The method `SendDataSet` on the `DataSetUtilities` class implements a general-purpose way to transmit the contents of a `DataSet` instance to the client.</span></span> <span data-ttu-id="b86c1-107">`DoTest` クラスで定義されている `TestSendDataSet` メソッドは、`SendDataSet` を作成し、Transact-SQL ストアド プロシージャ `DataSet` から返されたデータを設定することによって、`uspGetTwoBOMTestData` メソッドの動作を検証します。</span><span class="sxs-lookup"><span data-stu-id="b86c1-107">The `DoTest` method that is defined on the `TestSendDataSet` class verifies that the `SendDataSet` method works by creating a `DataSet` and filling it with data from the `uspGetTwoBOMTestData` Transact-SQL stored procedure.</span></span> <span data-ttu-id="b86c1-108">`uspGetTwoBOMTestData` は、Transact-SQL ストアド プロシージャ `uspGetBillOfMaterials` を 2 回実行し、`usp_GetTwoBOMTestData` ストアド プロシージャへのパラメーターとして指定された 2 つの製品の部品表に対して再帰的にクエリを行います。</span><span class="sxs-lookup"><span data-stu-id="b86c1-108">The `uspGetTwoBOMTestData` runs the Transact-SQL stored procedure `uspGetBillOfMaterials` twice to recursively query for the bill of materials for two products specified as parameters to the `usp_GetTwoBOMTestData` stored procedure.</span></span> <span data-ttu-id="b86c1-109">データセットに設定されたデータは、`SendDataSet` 呼び出しにより結果セットとしてクライアントへ配信される前に、変更されるのが普通です。</span><span class="sxs-lookup"><span data-stu-id="b86c1-109">Ordinarily, after filling the data set, the data would be modified before invoking `SendDataSet` to deliver the data within the data set as a result set to the client.</span></span> <span data-ttu-id="b86c1-110">わかりやすくするために、このサンプルではデータを変更せずに返します。</span><span class="sxs-lookup"><span data-stu-id="b86c1-110">For simplicity, this sample returns the data without modification.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b86c1-111">前提条件</span><span class="sxs-lookup"><span data-stu-id="b86c1-111">Prerequisites</span></span>  
 <span data-ttu-id="b86c1-112">このプロジェクトを作成して実行するには、次のソフトウェアがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b86c1-112">To create and run this project the following the following software must be installed:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b86c1-113">または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express。</span><span class="sxs-lookup"><span data-stu-id="b86c1-113">or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express.</span></span> <span data-ttu-id="b86c1-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express ドキュメントとサンプルの [Web サイト](https://www.microsoft.com/sql-server/sql-server-editions-express)から無償で入手できます。</span><span class="sxs-lookup"><span data-stu-id="b86c1-114">You can obtain [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express free of charge from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express Documentation and Samples [Web site](https://www.microsoft.com/sql-server/sql-server-editions-express)</span></span>  
  
-   <span data-ttu-id="b86c1-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] デベロッパー [Web サイト](https://go.microsoft.com/fwlink/?linkid=62796)から入手できる AdventureWorks データベース。</span><span class="sxs-lookup"><span data-stu-id="b86c1-115">The AdventureWorks database that is available at the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Developer [Web site](https://go.microsoft.com/fwlink/?linkid=62796)</span></span>  
  
-   <span data-ttu-id="b86c1-116">.NET Framework SDK 2.0 以降または Microsoft Visual Studio 2005 以降。</span><span class="sxs-lookup"><span data-stu-id="b86c1-116">.NET Framework SDK 2.0 or later or Microsoft Visual Studio 2005 or later.</span></span> <span data-ttu-id="b86c1-117">.NET Framework SDK は無償で入手できます。</span><span class="sxs-lookup"><span data-stu-id="b86c1-117">You can obtain .NET Framework SDK free of charge.</span></span>  
  
-   <span data-ttu-id="b86c1-118">また、次の条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b86c1-118">In addition, the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="b86c1-119">使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスで CLR 統合が有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b86c1-119">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using must have CLR integration enabled.</span></span>  
  
-   <span data-ttu-id="b86c1-120">CLR 統合を有効にするには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="b86c1-120">In order to enable CLR integration, perform the following steps:</span></span>  
  
    #### <a name="enabling-clr-integration"></a><span data-ttu-id="b86c1-121">CLR 統合の有効化</span><span class="sxs-lookup"><span data-stu-id="b86c1-121">Enabling CLR Integration</span></span>  
  
    -   <span data-ttu-id="b86c1-122">以下の [!INCLUDE[tsql](../../includes/tsql-md.md)] コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="b86c1-122">Execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] commands:</span></span>  
  
     `sp_configure 'clr enabled', 1`  
  
     `GO`  
  
     `RECONFIGURE`  
  
     `GO`  
  
    > [!NOTE]  
    >  <span data-ttu-id="b86c1-123">CLR を有効にするには、 `ALTER SETTINGS` サーバーレベルの権限が必要です。この権限は、 `sysadmin` 固定サーバーロールおよびのメンバーによって暗黙的に保持されてい `serveradmin` ます。</span><span class="sxs-lookup"><span data-stu-id="b86c1-123">To enable CLR, you must have `ALTER SETTINGS` server level permission, which is implicitly held by members of the `sysadmin` and `serveradmin` fixed server roles.</span></span>  
  
-   <span data-ttu-id="b86c1-124">使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに AdventureWorks データベースがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b86c1-124">The AdventureWorks database must be installed on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using.</span></span>  
  
-   <span data-ttu-id="b86c1-125">使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの管理者でない場合は、インストールを完了するために **CreateAssembly** 権限が管理者から付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b86c1-125">If you are not an administrator for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using, you must have an administrator grant you **CreateAssembly**  permission to complete the installation.</span></span>  
  
## <a name="building-the-sample"></a><span data-ttu-id="b86c1-126">サンプルのビルド</span><span class="sxs-lookup"><span data-stu-id="b86c1-126">Building the Sample</span></span>  
  
#### <a name="create-and-run-the-sample-by-using-the-following-instructions"></a><span data-ttu-id="b86c1-127">次の手順に従ってサンプルを作成し、実行します。</span><span class="sxs-lookup"><span data-stu-id="b86c1-127">Create and run the sample by using the following instructions:</span></span>  
  
1.  <span data-ttu-id="b86c1-128">Visual Studio または .NET Framework のコマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="b86c1-128">Open a Visual Studio or .NET Framework command prompt.</span></span>  
  
2.  <span data-ttu-id="b86c1-129">必要な場合は、サンプル用のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="b86c1-129">If necessary, create a directory for your sample.</span></span> <span data-ttu-id="b86c1-130">この例では C:\MySample を使用します。</span><span class="sxs-lookup"><span data-stu-id="b86c1-130">For this example, we will use C:\MySample.</span></span>  
  
3.  <span data-ttu-id="b86c1-131">c:\MySample で、`SendDataSet.vb` (Visual Basic サンプル) または `SendDataSet.cs` (C# サンプル) を作成し、適切な Visual Basic または C# のサンプル コード (下記) をこのファイルにコピーします。</span><span class="sxs-lookup"><span data-stu-id="b86c1-131">In c:\MySample, create `SendDataSet.vb` (for the Visual Basic sample) or `SendDataSet.cs` (for the C# sample) and copy the appropriate Visual Basic or C# sample code (below) into the file.</span></span>  
  
4.  <span data-ttu-id="b86c1-132">選択した言語に応じて次のいずれかをコマンド プロンプトで実行し、サンプル コードを必要なアセンブリにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="b86c1-132">Compile the sample code into the required assembly from the command line prompt by executing one of the following, depending on your choice of language.</span></span>  
  
    -   `Vbc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Xml.dll  /target:library SendDataSet.vb`  
  
    -   `Csc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Xml.dll /target:library SendDataSet.cs`  
  
5.  <span data-ttu-id="b86c1-133">[!INCLUDE[tsql](../../includes/tsql-md.md)] インストール コードをファイルにコピーし、`Install.sql` としてサンプル ディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="b86c1-133">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation code into a file and save it as `Install.sql` in the sample directory.</span></span>  
  
6.  <span data-ttu-id="b86c1-134">サンプルが `C:\MySample\`以外のディレクトリにインストールされている場合は、その場所を示すように、ファイル `Install.sql` を編集します。</span><span class="sxs-lookup"><span data-stu-id="b86c1-134">If the sample is installed in a directory other then `C:\MySample\`, edit the file `Install.sql` as indicated to point to that location.</span></span>  
  
7.  <span data-ttu-id="b86c1-135">次のコマンドを実行して、アセンブリ、ストアド プロシージャ、および関数を配置します。</span><span class="sxs-lookup"><span data-stu-id="b86c1-135">Deploy the assembly, stored procedure and functions by executing</span></span>  
  
    -   `sqlcmd -E -I -i install.sql`  
  
8.  <span data-ttu-id="b86c1-136">[!INCLUDE[tsql](../../includes/tsql-md.md)] テスト スクリプトをファイルにコピーし、`test.sql` としてサンプル ディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="b86c1-136">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] test script into a file and save it as `test.sql` in the sample directory.</span></span>  
  
    -   `sqlcmd -E -I -i test.sql`  
  
9. <span data-ttu-id="b86c1-137">[!INCLUDE[tsql](../../includes/tsql-md.md)] クリーンアップ スクリプトをファイルにコピーし、`cleanup.sql` としてサンプル ディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="b86c1-137">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] cleanup script into a file and save it as `cleanup.sql` in the sample directory.</span></span>  
  
10. <span data-ttu-id="b86c1-138">次のコマンドを使用してこのスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="b86c1-138">Execute the script with the  following command</span></span>  
  
    -   `sqlcmd -E -I -i cleanup.sql`  
  
## <a name="sample-code"></a><span data-ttu-id="b86c1-139">サンプル コード</span><span class="sxs-lookup"><span data-stu-id="b86c1-139">Sample Code</span></span>  
 <span data-ttu-id="b86c1-140">このサンプルのコード リストを次に示します。</span><span class="sxs-lookup"><span data-stu-id="b86c1-140">The following are the code listings for this sample.</span></span>  
  
 <span data-ttu-id="b86c1-141">C#</span><span class="sxs-lookup"><span data-stu-id="b86c1-141">C#</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
  
    public static class DataSetUtilities  
    {  
  
        public static void SendDataSet(DataSet ds)  
        {  
            if (ds == null)  
            {  
                throw new ArgumentException("SendDataSet requires a non-null data set.");  
            }  
            else  
            {  
                foreach (DataTable dt in ds.Tables)  
                {  
                    SendDataTable(dt);  
                }  
            }  
        }  
  
        public static void SendDataTable(DataTable dt)  
        {  
            bool[] coerceToString;  // Do we need to coerce this column to string?  
            SqlMetaData[] metaData = ExtractDataTableColumnMetaData(dt, out coerceToString);  
  
            SqlDataRecord record = new SqlDataRecord(metaData);  
            SqlPipe pipe = SqlContext.Pipe;  
            pipe.SendResultsStart(record);  
            try  
            {  
                foreach (DataRow row in dt.Rows)  
                {  
                    for (int index = 0; index < record.FieldCount; index++)  
                    {  
                        object value = row[index];  
                        if (null != value && coerceToString[index])  
                            value = value.ToString();  
                        record.SetValue(index, value);  
                    }  
  
                    pipe.SendResultsRow(record);  
                }  
            }  
            finally  
            {  
                pipe.SendResultsEnd();  
            }  
        }  
  
        private static SqlMetaData[] ExtractDataTableColumnMetaData(DataTable dt, out bool[] coerceToString)  
        {  
            SqlMetaData[] metaDataResult = new SqlMetaData[dt.Columns.Count];  
            coerceToString = new bool[dt.Columns.Count];  
            for (int index = 0; index < dt.Columns.Count; index++)  
            {  
                DataColumn column = dt.Columns[index];  
                metaDataResult[index] = SqlMetaDataFromColumn(column, out coerceToString[index]);  
            }  
  
            return metaDataResult;  
        }  
  
        private static Exception InvalidDataTypeCode(TypeCode code)  
        {  
            return new ArgumentException("Invalid type: " + code);  
        }  
  
        private static Exception UnknownDataType(Type clrType)  
        {  
            return new ArgumentException("Unknown type: " + clrType);  
        }  
  
        private static SqlMetaData SqlMetaDataFromColumn(DataColumn column, out bool coerceToString)  
        {  
            coerceToString = false;  
            SqlMetaData sql_md = null;  
            Type clrType = column.DataType;  
            string name = column.ColumnName;  
            switch (Type.GetTypeCode(clrType))  
            {  
                case TypeCode.Boolean: sql_md = new SqlMetaData(name, SqlDbType.Bit); break;  
                case TypeCode.Byte: sql_md = new SqlMetaData(name, SqlDbType.TinyInt); break;  
                case TypeCode.Char: sql_md = new SqlMetaData(name, SqlDbType.NVarChar, 1); break;  
                case TypeCode.DateTime: sql_md = new SqlMetaData(name, SqlDbType.DateTime); break;  
                case TypeCode.DBNull: throw InvalidDataTypeCode(TypeCode.DBNull);  
                case TypeCode.Decimal: sql_md = new SqlMetaData(name, SqlDbType.Decimal, 18, 0); break;  
                case TypeCode.Double: sql_md = new SqlMetaData(name, SqlDbType.Float); break;  
                case TypeCode.Empty: throw InvalidDataTypeCode(TypeCode.Empty);  
                case TypeCode.Int16: sql_md = new SqlMetaData(name, SqlDbType.SmallInt); break;  
                case TypeCode.Int32: sql_md = new SqlMetaData(name, SqlDbType.Int); break;  
                case TypeCode.Int64: sql_md = new SqlMetaData(name, SqlDbType.BigInt); break;  
                case TypeCode.SByte: throw InvalidDataTypeCode(TypeCode.SByte);  
                case TypeCode.Single: sql_md = new SqlMetaData(name, SqlDbType.Real); break;  
                case TypeCode.String: sql_md = new SqlMetaData(name, SqlDbType.NVarChar, column.MaxLength);  
                    break;  
                case TypeCode.UInt16: throw InvalidDataTypeCode(TypeCode.UInt16);  
                case TypeCode.UInt32: throw InvalidDataTypeCode(TypeCode.UInt32);  
                case TypeCode.UInt64: throw InvalidDataTypeCode(TypeCode.UInt64);  
                case TypeCode.Object:  
                    sql_md = SqlMetaDataFromObjectColumn(name, column, clrType);  
                    if (sql_md == null)  
                    {  
                        // Unknown type, try to treat it as string;  
                        sql_md = new SqlMetaData(name, SqlDbType.NVarChar, column.MaxLength);  
                        coerceToString = true;  
                    }  
                    break;  
  
                default: throw UnknownDataType(clrType);  
            }  
  
            return sql_md;  
        }  
  
        private static SqlMetaData SqlMetaDataFromObjectColumn(string name, DataColumn column, Type clrType)  
        {  
            SqlMetaData sql_md = null;  
            if (clrType == typeof(System.Byte[]) || clrType == typeof(SqlBinary) || clrType == typeof(SqlBytes) ||  
        clrType == typeof(System.Char[]) || clrType == typeof(SqlString) || clrType == typeof(SqlChars))  
                sql_md = new SqlMetaData(name, SqlDbType.VarBinary, column.MaxLength);  
            else if (clrType == typeof(System.Guid))  
                sql_md = new SqlMetaData(name, SqlDbType.UniqueIdentifier);  
            else if (clrType == typeof(System.Object))  
                sql_md = new SqlMetaData(name, SqlDbType.Variant);  
            else if (clrType == typeof(SqlBoolean))  
                sql_md = new SqlMetaData(name, SqlDbType.Bit);  
            else if (clrType == typeof(SqlByte))  
                sql_md = new SqlMetaData(name, SqlDbType.TinyInt);  
            else if (clrType == typeof(SqlDateTime))  
                sql_md = new SqlMetaData(name, SqlDbType.DateTime);  
            else if (clrType == typeof(SqlDouble))  
                sql_md = new SqlMetaData(name, SqlDbType.Float);  
            else if (clrType == typeof(SqlGuid))  
                sql_md = new SqlMetaData(name, SqlDbType.UniqueIdentifier);  
            else if (clrType == typeof(SqlInt16))  
                sql_md = new SqlMetaData(name, SqlDbType.SmallInt);  
            else if (clrType == typeof(SqlInt32))  
                sql_md = new SqlMetaData(name, SqlDbType.Int);  
            else if (clrType == typeof(SqlInt64))  
                sql_md = new SqlMetaData(name, SqlDbType.BigInt);  
            else if (clrType == typeof(SqlMoney))  
                sql_md = new SqlMetaData(name, SqlDbType.Money);  
            else if (clrType == typeof(SqlDecimal))  
                sql_md = new SqlMetaData(name, SqlDbType.Decimal, SqlDecimal.MaxPrecision, 0);  
            else if (clrType == typeof(SqlSingle))  
                sql_md = new SqlMetaData(name, SqlDbType.Real);  
            else if (clrType == typeof(SqlXml))  
                sql_md = new SqlMetaData(name, SqlDbType.Xml);  
            else  
                sql_md = null;  
  
            return sql_md;  
        }  
  
    }  
 public static class TestSendDataSet  
    {  
        private const string TestConnectionString = "context connection=true";  
        const int prod1ID = 750; //Product ID of Road-150 Red, 44 bicycle  
        const int prod2ID = 751; //Product ID of Road-150 Red, 48 bicycle  
  
        /// <summary>  
        /// Invoke a stored procedure to get some bill of material information and   
        /// fill a data set with the two result sets.  Return the data set to the client.  
        /// </summary>  
        public static void DoTest()  
        {  
            using (SqlConnection conn = new SqlConnection(TestConnectionString))  
            {  
                SqlCommand cmd = conn.CreateCommand();  
                cmd.CommandText = "usp_GetTwoBOMTestData";  
                cmd.CommandType = CommandType.StoredProcedure;  
  
                SqlParameter prod1Param = new SqlParameter("@ProductID1", SqlDbType.Int);  
                prod1Param.Value = prod1ID;  
                cmd.Parameters.Add(prod1Param);  
  
                SqlParameter prod2Param = new SqlParameter("@ProductID2", SqlDbType.Int);  
                prod2Param.Value = prod2ID;  
                cmd.Parameters.Add(prod2Param);  
  
                SqlParameter asOfDateParam = new SqlParameter("@AsOfDate", SqlDbType.DateTime);  
                asOfDateParam.Value = DateTime.Now;  
                cmd.Parameters.Add(asOfDateParam);  
  
                DataSet ds = new DataSet("TestData");  
                SqlDataAdapter sda = new SqlDataAdapter(cmd);  
                conn.Open();  
                sda.Fill(ds);  
  
// Normally, after filling the data set, rather than immediately returning it,   
// the data would be modified before invoking SendDataSet to deliver   
// the data within the data set as a result set to the client.  For simplicity   
// this sample simply returns the data.  
  
                DataSetUtilities.SendDataSet(ds);  
  
            }  
        }  
  
    }  
```  
  
 <span data-ttu-id="b86c1-142">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b86c1-142">Visual Basic</span></span>  
  
```  
Imports Microsoft.VisualBasic  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Diagnostics  
Imports System.Collections.Generic  
Imports System.Text  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Runtime.InteropServices  
  
Public Class DataSetUtilities  
  
    Public Shared Sub SendDataSet(ByVal ds As DataSet)  
        If ds Is Nothing Then  
            Throw New ArgumentException("SendDataSet requires a non-null data set.")  
        Else  
            For Each dt As DataTable In ds.Tables  
                SendDataTable(dt)  
            Next  
        End If  
    End Sub  
  
    Public Shared Sub SendDataTable(ByVal dt As DataTable)  
        Dim coerceToString() As Boolean = Nothing ' Do we need to coerce this column to string?  
        Dim metaData As SqlMetaData() = ExtractDataTableColumnMetaData(dt, coerceToString)  
  
        Dim record As New SqlDataRecord(metaData)  
        Dim pipe As SqlPipe = SqlContext.Pipe  
        pipe.SendResultsStart(record)  
  
        Try  
            For Each row As DataRow In dt.Rows  
                For index As Integer = 0 To record.FieldCount - 1  
                    Dim value As Object = row(index)  
                    If Nothing Is value AndAlso coerceToString(index) Then  
                        value = value.ToString()  
                    End If  
  
                    record.SetValue(index, value)  
                Next  
  
                pipe.SendResultsRow(record)  
            Next  
        Finally  
            pipe.SendResultsEnd()  
        End Try  
    End Sub  
  
    Private Shared Function ExtractDataTableColumnMetaData(ByVal dt As DataTable, <Out()> ByRef coerceToString() As Boolean) As SqlMetaData()  
        Dim metaDataResult(dt.Columns.Count - 1) As SqlMetaData  
        coerceToString = New Boolean(dt.Columns.Count - 1) {}  
        For index As Integer = 0 To dt.Columns.Count - 1  
            Dim column As DataColumn = dt.Columns(index)  
            metaDataResult(index) = SqlMetaDataFromColumn(column, coerceToString(index))  
        Next  
  
        Return metaDataResult  
    End Function  
    Private Shared Function InvalidDataTypeCode(ByVal code As TypeCode) As Exception  
        Return New ArgumentException("Invalid type: " & code.ToString())  
    End Function  
  
    Private Shared Function UnknownDataType(ByVal clrType As Type) As Exception  
        Return New ArgumentException("Unknown type: " & clrType.ToString())  
    End Function  
  
    Private Shared Function SqlMetaDataFromColumn(ByVal column As DataColumn, ByRef coerceToString As Boolean) As SqlMetaData  
        coerceToString = False  
        Dim sql_md As SqlMetaData = Nothing  
        Dim clrType As Type = column.DataType  
        Dim name As String = column.ColumnName  
        Select Case Type.GetTypeCode(clrType)  
            Case TypeCode.Boolean  
                sql_md = New SqlMetaData(name, SqlDbType.Bit)  
            Case TypeCode.Byte  
                sql_md = New SqlMetaData(name, SqlDbType.TinyInt)  
            Case TypeCode.Char  
                sql_md = New SqlMetaData(name, SqlDbType.NVarChar, 1)  
            Case TypeCode.DateTime  
                sql_md = New SqlMetaData(name, SqlDbType.DateTime)  
            Case TypeCode.DBNull  
                Throw InvalidDataTypeCode(TypeCode.DBNull)  
            Case TypeCode.Decimal  
                sql_md = New SqlMetaData(name, SqlDbType.Decimal)  
            Case TypeCode.Double  
                sql_md = New SqlMetaData(name, SqlDbType.Float)  
            Case TypeCode.Empty  
                Throw InvalidDataTypeCode(TypeCode.Empty)  
            Case TypeCode.Int16  
                sql_md = New SqlMetaData(name, SqlDbType.SmallInt)  
            Case TypeCode.Int32  
                sql_md = New SqlMetaData(name, SqlDbType.Int)  
            Case TypeCode.Int64  
                sql_md = New SqlMetaData(name, SqlDbType.BigInt)  
            Case TypeCode.SByte  
                Throw InvalidDataTypeCode(TypeCode.SByte)  
            Case TypeCode.Single  
                sql_md = New SqlMetaData(name, SqlDbType.Real)  
            Case TypeCode.String  
                sql_md = New SqlMetaData(name, SqlDbType.NVarChar, column.MaxLength)  
            Case TypeCode.UInt16  
                Throw InvalidDataTypeCode(TypeCode.UInt16)  
            Case TypeCode.UInt32  
                Throw InvalidDataTypeCode(TypeCode.UInt32)  
            Case TypeCode.UInt64  
                Throw InvalidDataTypeCode(TypeCode.UInt64)  
            Case TypeCode.Object  
                sql_md = SqlMetaDataFromObjectColumn(name, column, clrType)  
                If sql_md Is Nothing Then  
                    ' Unknown type, try to treat it as string  
                    sql_md = New SqlMetaData(name, SqlDbType.NVarChar, column.MaxLength)  
                    coerceToString = True  
                End If  
            Case Else  
                Throw UnknownDataType(clrType)  
        End Select  
  
        Return sql_md  
    End Function  
  
    Private Shared Function SqlMetaDataFromObjectColumn(ByVal name As String, ByVal column As DataColumn, ByVal clrType As Type) As SqlMetaData  
        Dim sql_md As SqlMetaData = Nothing  
  
        If (clrType Is GetType(System.Byte()) OrElse clrType Is GetType(SqlBinary) OrElse clrType Is GetType(SqlBytes) _  
            OrElse clrType Is GetType(System.Char()) OrElse clrType Is GetType(SqlString) OrElse clrType Is GetType(SqlChars)) Then  
            sql_md = New SqlMetaData(name, SqlDbType.VarBinary, column.MaxLength)  
        ElseIf (clrType Is GetType(System.Guid)) Then  
            sql_md = New SqlMetaData(name, SqlDbType.UniqueIdentifier)  
        ElseIf (clrType Is GetType(System.Object)) Then  
            sql_md = New SqlMetaData(name, SqlDbType.Variant)  
        ElseIf (clrType Is GetType(SqlBoolean)) Then  
            sql_md = New SqlMetaData(name, SqlDbType.Bit)  
        ElseIf (clrType Is GetType(SqlByte)) Then  
            sql_md = New SqlMetaData(name, SqlDbType.TinyInt)  
        ElseIf (clrType Is GetType(SqlDateTime)) Then  
            sql_md = New SqlMetaData(name, SqlDbType.DateTime)  
        ElseIf (clrType Is GetType(SqlDouble)) Then  
            sql_md = New SqlMetaData(name, SqlDbType.Float)  
        ElseIf (clrType Is GetType(SqlGuid)) Then  
            sql_md = New SqlMetaData(name, SqlDbType.UniqueIdentifier)  
        ElseIf (clrType Is GetType(SqlInt16)) Then  
            sql_md = New SqlMetaData(name, SqlDbType.SmallInt)  
        ElseIf (clrType Is GetType(SqlInt32)) Then  
            sql_md = New SqlMetaData(name, SqlDbType.Int)  
        ElseIf (clrType Is GetType(SqlInt64)) Then  
            sql_md = New SqlMetaData(name, SqlDbType.BigInt)  
        ElseIf (clrType Is GetType(SqlMoney)) Then  
            sql_md = New SqlMetaData(name, SqlDbType.Money)  
        ElseIf (clrType Is GetType(SqlDecimal)) Then  
            sql_md = New SqlMetaData(name, SqlDbType.Decimal, SqlDecimal.MaxPrecision, 0)  
        ElseIf (clrType Is GetType(SqlSingle)) Then  
            sql_md = New SqlMetaData(name, SqlDbType.Real)  
        ElseIf (clrType Is GetType(SqlXml)) Then  
            sql_md = New SqlMetaData(name, SqlDbType.Xml)  
        Else  
            sql_md = Nothing  
        End If  
  
        Return sql_md  
    End Function  
End Class  
  
Public Class TestSendDataSet  
    Private Const TestConnectionString As String = "context connection=true"  
    Private Const prod1ID As Integer = 750  'Product ID of Road-150 Red, 44 bicycle  
    Private Const prod2ID As Integer = 751  'Product ID of Road-150 Red, 48 bicycle  
  
    ''' <summary>  
    ''' Invoke a stored procedure to get some bill of material information and   
    ''' fill a data set with the two result sets.  Return the data set to the client.  
  
    <SqlProcedure(Name:="usp_TestSendDataSet")> _  
    Public Shared Sub DoTest()  
        Dim conn As New SqlConnection(TestConnectionString)  
        Try  
            Dim cmd As SqlCommand = conn.CreateCommand()  
            cmd.CommandText = "usp_GetTwoBOMTestData"  
            cmd.CommandType = CommandType.StoredProcedure  
  
            Dim prod1Param As New SqlParameter("@ProductID1", SqlDbType.Int)  
            prod1Param.Value = prod1ID  
            cmd.Parameters.Add(prod1Param)  
  
            Dim prod2Param As New SqlParameter("@ProductID2", SqlDbType.Int)  
            prod2Param.Value = prod2ID  
            cmd.Parameters.Add(prod2Param)  
  
            Dim asOfDateParam As New SqlParameter("@AsOfDate", SqlDbType.DateTime)  
            asOfDateParam.Value = DateTime.Now  
            cmd.Parameters.Add(asOfDateParam)  
  
            Dim ds As New DataSet("TestData")  
            Dim sda As New SqlDataAdapter(cmd)  
            conn.Open()  
            sda.Fill(ds)  
  
            ' Normally, after filling the data set, rather than immediately returning it,   
            ' the data would be modified before invoking SendDataSet to deliver   
            ' the data within the data set as a result set to the client.  For simplicity   
            ' this sample simply returns the data.  
            DataSetUtilities.SendDataSet(ds)  
        Finally  
            conn.Dispose()  
        End Try  
    End Sub  
End Class  
  
```  
  
 <span data-ttu-id="b86c1-143">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] インストール スクリプト (`Install.sql`) は、アセンブリを展開し、ストアド プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="b86c1-143">This is the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation script (`Install.sql`), which deploys the assembly and creates the stored procedures.</span></span>  
  
```  
USE AdventureWorks;  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'usp_GetTwoBOMTestData')  
DROP PROCEDURE usp_GetTwoBOMTestData;  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'usp_TestSendDataSet')  
DROP PROCEDURE usp_TestSendDataSet;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE name = N'SendDataSet')   
DROP ASSEMBLY SendDataSet;  
GO  
  
-- Procedure used to generate test data to fill the data set being returned to the client  
CREATE PROCEDURE usp_GetTwoBOMTestData  
(  
@ProductID1 int,  
@ProductID2 int,  
@AsOfDate DateTime  
)  
AS  
BEGIN  
EXEC uspGetBillOfMaterials @ProductID1, @AsOfDate;  
EXEC uspGetBillOfMaterials @ProductID2, @AsOfDate;  
END;  
GO  
  
DECLARE @SamplesPath nvarchar(1024)  
-- You may need to modify the value of the this variable if you have installed the sample someplace other than the default location.  
Set @SamplesPath = N'C:\MySample\'  
  
CREATE ASSEMBLY SendDataSet from @SamplesPath +'SendDataSet.dll'  
WITH PERMISSION_SET = Safe;  
GO  
  
CREATE PROCEDURE usp_TestSendDataSet  
AS  
EXTERNAL NAME [SendDataSet].[TestSendDataSet].[DoTest];  
GO  
```  
  
 <span data-ttu-id="b86c1-144">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] テスト スクリプト (`test.sql`) は、サンプルをテストします。</span><span class="sxs-lookup"><span data-stu-id="b86c1-144">This is the [!INCLUDE[tsql](../../includes/tsql-md.md)] test script (`test.sql`), which tests the sample.</span></span>  
  
```  
USE AdventureWorks  
GO  
  
EXEC usp_TestSendDataSet  
GO  
```  
  
 <span data-ttu-id="b86c1-145">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] は、データベースからアセンブリとストアド プロシージャを削除します。</span><span class="sxs-lookup"><span data-stu-id="b86c1-145">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] removes the assembly and stored procedure from the database.</span></span>  
  
```  
USE AdventureWorks  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'usp_GetTwoBOMTestData')  
DROP PROCEDURE usp_GetTwoBOMTestData;  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'usp_TestSendDataSet')  
DROP PROCEDURE usp_TestSendDataSet;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE name = N'SendDataSet')   
DROP ASSEMBLY SendDataSet;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="b86c1-146">参照</span><span class="sxs-lookup"><span data-stu-id="b86c1-146">See Also</span></span>  
 [<span data-ttu-id="b86c1-147">CLR &#40;共通言語ランタイム&#41; 統合の使用シナリオと例</span><span class="sxs-lookup"><span data-stu-id="b86c1-147">Usage Scenarios and Examples for Common Language Runtime &#40;CLR&#41; Integration</span></span>](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  

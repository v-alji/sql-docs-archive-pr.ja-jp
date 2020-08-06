---
title: インプロセスデータアクセスのサンプル |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: 155be272-4f9a-4d86-9f4f-714c4f45b49a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 62201474be26abdc5fe6e8f470b4896d51b9b106
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742501"
---
# <a name="in-process-data-access-sample"></a><span data-ttu-id="514cf-102">インプロセス データ アクセス サンプル</span><span class="sxs-lookup"><span data-stu-id="514cf-102">In-Process Data Access Sample</span></span>
  <span data-ttu-id="514cf-103">`InProcessDataAccess` サンプルには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CLR インプロセス データ アクセス プロバイダーのさまざまな機能を示す、多数の単純な関数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="514cf-103">The `InProcessDataAccess` sample contains a number of simple functions that demonstrate various features of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CLR in-process data access provider.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="514cf-104">[前提条件]</span><span class="sxs-lookup"><span data-stu-id="514cf-104">Prerequisites</span></span>  
 <span data-ttu-id="514cf-105">このプロジェクトを作成して実行するには、次のソフトウェアがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="514cf-105">To create and run this project the following the following software must be installed:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="514cf-106">または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express。</span><span class="sxs-lookup"><span data-stu-id="514cf-106">or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express.</span></span> <span data-ttu-id="514cf-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express ドキュメントとサンプルの [Web サイト](https://www.microsoft.com/sql-server/sql-server-editions-express)から無償で入手できます。</span><span class="sxs-lookup"><span data-stu-id="514cf-107">You can obtain [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express free of charge from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express Documentation and Samples [Web site](https://www.microsoft.com/sql-server/sql-server-editions-express)</span></span>  
  
-   <span data-ttu-id="514cf-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] デベロッパー [Web サイト](https://go.microsoft.com/fwlink/?linkid=62796)から入手できる AdventureWorks データベース。</span><span class="sxs-lookup"><span data-stu-id="514cf-108">The AdventureWorks database that is available at the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Developer [Web site](https://go.microsoft.com/fwlink/?linkid=62796)</span></span>  
  
-   <span data-ttu-id="514cf-109">.NET Framework SDK 2.0 以降または Microsoft Visual Studio 2005 以降。</span><span class="sxs-lookup"><span data-stu-id="514cf-109">.NET Framework SDK 2.0 or later or Microsoft Visual Studio 2005 or later.</span></span> <span data-ttu-id="514cf-110">.NET Framework SDK は無償で入手できます。</span><span class="sxs-lookup"><span data-stu-id="514cf-110">You can obtain .NET Framework SDK free of charge.</span></span>  
  
-   <span data-ttu-id="514cf-111">また、次の条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="514cf-111">In addition, the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="514cf-112">使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスで CLR 統合が有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="514cf-112">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using must have CLR integration enabled.</span></span>  
  
-   <span data-ttu-id="514cf-113">CLR 統合を有効にするには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="514cf-113">In order to enable CLR integration, perform the following steps:</span></span>  
  
    #### <a name="enabling-clr-integration"></a><span data-ttu-id="514cf-114">CLR 統合の有効化</span><span class="sxs-lookup"><span data-stu-id="514cf-114">Enabling CLR Integration</span></span>  
  
    -   <span data-ttu-id="514cf-115">以下の [!INCLUDE[tsql](../../includes/tsql-md.md)] コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="514cf-115">Execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] commands:</span></span>  
  
     `sp_configure 'clr enabled', 1`  
  
     `GO`  
  
     `RECONFIGURE`  
  
     `GO`  
  
    > [!NOTE]  
    >  <span data-ttu-id="514cf-116">CLR を有効にするには、 `ALTER SETTINGS` サーバーレベルの権限が必要です。この権限は、 `sysadmin` 固定サーバーロールおよびのメンバーによって暗黙的に保持されてい `serveradmin` ます。</span><span class="sxs-lookup"><span data-stu-id="514cf-116">To enable CLR, you must have `ALTER SETTINGS` server level permission, which is implicitly held by members of the `sysadmin` and `serveradmin` fixed server roles.</span></span>  
  
-   <span data-ttu-id="514cf-117">使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに AdventureWorks データベースがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="514cf-117">The AdventureWorks database must be installed on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using.</span></span>  
  
-   <span data-ttu-id="514cf-118">使用しているインスタンスの管理者ではない場合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、インストールを完了するには、 **createassembly**アクセス許可を管理者に付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="514cf-118">If you are not an administrator for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using, you must have an administrator grant you **CreateAssembly** permission to complete the installation.</span></span>  
  
## <a name="building-the-sample"></a><span data-ttu-id="514cf-119">サンプルのビルド</span><span class="sxs-lookup"><span data-stu-id="514cf-119">Building the Sample</span></span>  
  
#### <a name="create-and-run-the-sample-by-using-the-following-instructions"></a><span data-ttu-id="514cf-120">次の手順に従ってサンプルを作成し、実行します。</span><span class="sxs-lookup"><span data-stu-id="514cf-120">Create and run the sample by using the following instructions:</span></span>  
  
1.  <span data-ttu-id="514cf-121">Visual Studio または .NET Framework のコマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="514cf-121">Open a Visual Studio or .NET Framework command prompt.</span></span>  
  
2.  <span data-ttu-id="514cf-122">必要な場合は、サンプル用のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="514cf-122">If necessary, create a directory for your sample.</span></span> <span data-ttu-id="514cf-123">この例では C:\MySample を使用します。</span><span class="sxs-lookup"><span data-stu-id="514cf-123">For this example, we will use C:\MySample.</span></span>  
  
3.  <span data-ttu-id="514cf-124">c:\MySample で、`inprocda.vb` (Visual Basic サンプル) または `inprocda.cs` (C# サンプル) を作成し、適切な Visual Basic または C# のサンプル コード (下記) をこのファイルにコピーします。</span><span class="sxs-lookup"><span data-stu-id="514cf-124">In c:\MySample, create `inprocda.vb` (for the Visual Basic sample) or `inprocda.cs` (for the C# sample) and copy the appropriate Visual Basic or C# sample code (below) into the file.</span></span>  
  
4.  <span data-ttu-id="514cf-125">選択した言語に応じて次のいずれかをコマンド プロンプトで実行し、サンプル コードを必要なアセンブリにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="514cf-125">Compile the sample code into the required assembly from the command line prompt by executing one of the following, depending on your choice of language.</span></span>  
  
    -   `Vbc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Xml.dll /target:library InProcDA.vb`  
  
    -   `Csc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.XML.dll /target:library inprocda.cs`  
  
5.  <span data-ttu-id="514cf-126">[!INCLUDE[tsql](../../includes/tsql-md.md)] インストール コードをファイルにコピーし、`Install.sql` としてサンプル ディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="514cf-126">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation code into a file and save it as `Install.sql` in the sample directory.</span></span>  
  
6.  <span data-ttu-id="514cf-127">サンプルが `C:\MySample\`以外のディレクトリにインストールされている場合は、その場所を示すように、ファイル `Install.sql` を編集します。</span><span class="sxs-lookup"><span data-stu-id="514cf-127">If the sample is installed in a directory other then `C:\MySample\`, edit the file `Install.sql` as indicated to point to that location.</span></span>  
  
7.  <span data-ttu-id="514cf-128">次のコマンドを実行して、アセンブリ、ストアド プロシージャ、および関数を配置します。</span><span class="sxs-lookup"><span data-stu-id="514cf-128">Deploy the assembly, stored procedure and functions by executing</span></span>  
  
    -   `sqlcmd -E -I -i install.sql`  
  
8.  <span data-ttu-id="514cf-129">[!INCLUDE[tsql](../../includes/tsql-md.md)] インストール コードをファイルにコピーし、`test.sql` としてサンプル ディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="514cf-129">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation code into a file and save it as `test.sql` in the sample directory.</span></span>  
  
9. <span data-ttu-id="514cf-130">次のコマンドをコマンド プロンプトで実行して、アプリケーションをテストします。</span><span class="sxs-lookup"><span data-stu-id="514cf-130">Test the application by executing the following line at the command prompt:</span></span>  
  
    -   `sqlcmd -E -I -i test.sql`  
  
10. <span data-ttu-id="514cf-131">[!INCLUDE[tsql](../../includes/tsql-md.md)] クリーンアップ スクリプトをファイルにコピーし、`cleanup.sql` としてサンプル ディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="514cf-131">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] cleanup script into a file and save it as `cleanup.sql` in the sample directory.</span></span>  
  
11. <span data-ttu-id="514cf-132">次のコマンドを使用してこのスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="514cf-132">Execute the script with the  following command</span></span>  
  
    -   `sqlcmd -E -I -i cleanup.sql`  
  
## <a name="sample-code"></a><span data-ttu-id="514cf-133">サンプル コード</span><span class="sxs-lookup"><span data-stu-id="514cf-133">Sample Code</span></span>  
 <span data-ttu-id="514cf-134">このサンプルのコード リストを次に示します。</span><span class="sxs-lookup"><span data-stu-id="514cf-134">The following are the code listings for this sample.</span></span>  
  
 <span data-ttu-id="514cf-135">C#</span><span class="sxs-lookup"><span data-stu-id="514cf-135">C#</span></span>  
  
```  
using System;  
using System.Data;  
using System.Data.Sql;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;  
public sealed class DataAccessDemo  
{  
        private DataAccessDemo()  
        {  
        }  
  
        /// <summary>  
/// Simple example to send a message to the client.  
/// </summary>  
public static void SendMessage(string msg)  
{  
SqlContext.Pipe.Send("Message from server: " + msg);  
}  
  
/// <summary>  
/// Simple example of performing data access within  
/// a function  
/// </summary>  
/// <returns></returns>  
        [Microsoft.SqlServer.Server.SqlFunction(DataAccess = Microsoft.SqlServer.Server.DataAccessKind.Read)]  
public static string ReportSqlVersion()  
{  
            using (SqlConnection conn = new SqlConnection("context connection=true"))  
            {  
                //create a command from the current context  
                SqlCommand cmd = conn.CreateCommand();  
  
                //execute something  
                cmd.CommandText = "select @@version";  
  
                conn.Open();  
                //return results as scalar  
                return (string)cmd.ExecuteScalar();  
            }  
}  
  
/// <summary>  
/// Create a result set on the fly and send it to the client.  
/// </summary>  
public static void SendTransientResultSet()  
{  
//create the metadata for the columns  
            Microsoft.SqlServer.Server.SqlMetaData[] columnSchema   
                = new Microsoft.SqlServer.Server.SqlMetaData[] {  
new Microsoft.SqlServer.Server.SqlMetaData("stringcol", SqlDbType.NVarChar, 128)  
};  
  
//create a record based on that metadata  
            SqlDataRecord newRecord = new SqlDataRecord(columnSchema);  
  
//populate it  
newRecord.SetString(0, "Hello World!");  
  
//send it  
SqlContext.Pipe.Send(newRecord);  
}  
  
/// <summary>  
/// Execute a command and send the results to the client directly.  
/// </summary>  
public static void ExecuteToClient()  
{  
            using (SqlConnection conn = new SqlConnection("context connection=true"))  
            {  
                SqlCommand cmd = conn.CreateCommand();  
  
                cmd.CommandText = "select @@version";  
                conn.Open();  
                SqlContext.Pipe.ExecuteAndSend(cmd);  
            }  
}  
  
/// <summary>  
/// Execute a command and send the resultig reader to the client  
/// </summary>  
public static void SendReaderToClient()  
{  
            using (SqlConnection conn = new SqlConnection("context connection=true"))  
            {  
                SqlCommand cmd = conn.CreateCommand();  
  
                cmd.CommandText = "select @@version";  
                conn.Open();  
                SqlDataReader rdr = cmd.ExecuteReader();  
                try  
                {  
                    SqlContext.Pipe.Send(rdr);  
                }  
                finally  
                {  
                    rdr.Close();  
                }  
            }  
}  
  
};  
```  
  
 <span data-ttu-id="514cf-136">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="514cf-136">Visual Basic</span></span>  
  
```  
Imports Microsoft.SqlServer.Server  
Imports Microsoft.VisualBasic  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Diagnostics  
Partial Public NotInheritable Class DataAccessDemo  
    Private Sub New()  
    End Sub  
  
    ''' <summary>  
    ''' Simple example of performing data access within a function  
    ''' </summary>  
    ''' <returns></returns>  
    <SqlFunction(DataAccess:=DataAccessKind.Read)> _  
    Public Shared Function ReportSqlVersion() As SqlString  
        Using conn As New SqlConnection("context connection=true")  
            'create a command from the current context  
            Dim cmd As SqlCommand = conn.CreateCommand()  
  
            'execute something  
            cmd.CommandText = "SELECT @@VERSION"  
  
            conn.Open()  
  
            'return results as scalar  
            Return CType(cmd.ExecuteScalar(), String)  
        End Using  
    End Function  
  
    ''' <summary>  
    ''' Simple example to send a message to the client.  
    ''' </summary>  
    Public Shared Sub SendMessage(ByVal msg As String)  
        SqlContext.Pipe.Send(("Message from server: " & msg))  
    End Sub  
  
    ''' <summary>  
    ''' Create a result set on the fly and send it to the client.  
    ''' </summary>  
    Public Shared Sub SendTransientResultSet()  
        'create the metadata for the columns  
        Dim columnSchema() As Microsoft.SqlServer.Server.SqlMetaData _  
            = {New SqlMetaData("stringcol", SqlDbType.NVarChar, 128)}  
  
        'create a record based on that metadata  
        Dim newRecord As New SqlDataRecord(columnSchema)  
  
        'populate it  
        newRecord.SetString(0, "Hello World!")  
  
        'send it  
        SqlContext.Pipe.Send(newRecord)  
    End Sub  
  
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    Public Shared Sub ExecuteToClient()  
        Using conn As New SqlConnection("context connection=true")  
            Dim cmd As SqlCommand = conn.CreateCommand()  
  
            cmd.CommandText = "SELECT @@VERSION"  
            conn.Open()  
            SqlContext.Pipe.ExecuteAndSend(cmd)  
        End Using  
    End Sub  
  
    ''' <summary>  
    ''' Execute a command and send the resulting reader to the client  
    ''' </summary>  
    Public Shared Sub SendReaderToClient()  
        Using conn As New SqlConnection("context connection=true")  
            Dim cmd As SqlCommand = conn.CreateCommand()  
            cmd.CommandText = "SELECT @@VERSION"  
            conn.Open()  
            Dim rdr As SqlDataReader = cmd.ExecuteReader()  
            Try  
                SqlContext.Pipe.Send(rdr)  
            Finally  
                rdr.Close()  
            End Try  
        End Using  
    End Sub  
  
End Class  
  
```  
  
 <span data-ttu-id="514cf-137">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] インストール スクリプト (`Install.sql`) は、アセンブリを配置し、この例で必要なストアド プロシージャと関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="514cf-137">This is the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation script (`Install.sql`), which deploys the assembly and creates the stored procedures and function required by this example.</span></span>  
  
```  
USE AdventureWorks;  
GO  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'SendMessage')  
DROP PROCEDURE SendMessage;  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'SendTransientResultSet')  
DROP PROCEDURE SendTransientResultSet;  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'ExecuteToClient')  
DROP PROCEDURE ExecuteToClient;  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'SendReaderToClient')  
DROP PROCEDURE SendReaderToClient;  
GO  
  
IF EXISTS (SELECT * FROM sys.objects WHERE name = N'ReportSqlVersion' and (type = 'FS' or type = 'FT'))    
DROP FUNCTION [ReportSqlVersion];  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE name = N'InProcDA') DROP ASSEMBLY InProcDA;  
GO  
DECLARE @SamplesPath nvarchar(1024)  
  
-- You may need to modify the value of the this variable if you have installed the sample someplace other than the default location.  
set @SamplesPath = N'C:\MySample\'  
CREATE ASSEMBLY InProcDA FROM @SamplesPath + 'InProcDA.dll'  
WITH permission_set = SAFE;  
GO  
  
CREATE PROCEDURE [SendMessage] @msg nvarchar(4000)  
AS  
EXTERNAL NAME [InProcDA].[DataAccessDemo].[SendMessage];  
GO  
  
CREATE FUNCTION [ReportSqlVersion]() RETURNS nvarchar(4000)  
AS EXTERNAL NAME [InProcDA].[DataAccessDemo].[ReportSqlVersion];  
GO  
  
CREATE PROCEDURE [SendTransientResultSet]  
AS  
EXTERNAL NAME [InProcDA].[DataAccessDemo].[SendTransientResultSet];  
GO  
  
CREATE PROCEDURE [ExecuteToClient]  
AS  
EXTERNAL NAME [InProcDA].[DataAccessDemo].[ExecuteToClient];  
GO  
  
CREATE PROCEDURE [SendReaderToClient]  
AS  
EXTERNAL NAME [InProcDA].[DataAccessDemo].[SendReaderToClient];  
GO  
```  
  
 <span data-ttu-id="514cf-138">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ( `test.sql` ) は、このサンプルで定義されているストアドプロシージャと関数を使用して、この例をテストします。</span><span class="sxs-lookup"><span data-stu-id="514cf-138">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] (`test.sql`) tests the example by exercising the stored procedures and function defined in this sample.</span></span>  
  
```  
USE AdventureWorks;  
GO  
  
-- send a message to the client  
EXEC SendMessage  N'This is a test message.';  
  
-- exec a function that does data access  
SELECT dbo.ReportSqlVersion();  
  
-- exec the proc that sends a result set to the client  
EXEC SendTransientResultSet;  
  
EXEC ExecuteToClient;  
  
EXEC SendReaderToClient;  
  
USE master;  
GO  
  
```  
  
 <span data-ttu-id="514cf-139">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] は、データベースからアセンブリ、関数、およびストアド プロシージャを削除します。</span><span class="sxs-lookup"><span data-stu-id="514cf-139">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] removes the assembly, function and stored procedures from the database.</span></span>  
  
```  
  
USE AdventureWorks  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'SendMessage')  
DROP PROCEDURE SendMessage;  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'SendTransientResultSet')  
DROP PROCEDURE SendTransientResultSet;  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'ExecuteToClient')  
DROP PROCEDURE ExecuteToClient;  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'SendReaderToClient')  
DROP PROCEDURE SendReaderToClient;  
GO  
  
IF EXISTS (SELECT * FROM sys.objects WHERE name = N'ReportSqlVersion' and (type = 'FS' or type = 'FT'))    
DROP FUNCTION [ReportSqlVersion];  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE name = N'InProcDA') DROP ASSEMBLY InProcDA;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="514cf-140">参照</span><span class="sxs-lookup"><span data-stu-id="514cf-140">See Also</span></span>  
 [<span data-ttu-id="514cf-141">CLR &#40;共通言語ランタイム&#41; 統合の使用シナリオと例</span><span class="sxs-lookup"><span data-stu-id="514cf-141">Usage Scenarios and Examples for Common Language Runtime &#40;CLR&#41; Integration</span></span>](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  

---
title: ユーザー定義関数の作成、変更、および削除 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- user-defined functions [SMO]
ms.assetid: 0ebebd3b-0775-41c2-989d-aa4cf81af12a
author: stevestein
ms.author: sstein
ms.openlocfilehash: b9ff6d1b6e675d41e96f26fc24e6e0dd4ba69454
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644942"
---
# <a name="creating-altering-and-removing-user-defined-functions"></a><span data-ttu-id="22edb-102">ユーザー定義関数の作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="22edb-102">Creating, Altering, and Removing User-Defined Functions</span></span>
  <span data-ttu-id="22edb-103">オブジェクトは、 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> ユーザーがのユーザー定義関数をプログラムで管理できるようにする機能を提供し [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="22edb-103">The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> object provides functionality that lets users programmatically manage user-defined functions in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="22edb-104">ユーザー定義関数では、入力パラメーターおよび出力パラメーターに加えて、テーブル列への直接参照もサポートされます。</span><span class="sxs-lookup"><span data-stu-id="22edb-104">User-defined functions support input and output parameters, and also support direct references to table columns.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="22edb-105">では、ストアド プロシージャ、ユーザー定義関数、トリガー、およびユーザー定義データ型内でアセンブリを使用できるようにするには、アセンブリがデータベース内に登録される必要があります。</span><span class="sxs-lookup"><span data-stu-id="22edb-105">requires assemblies to be registered within a database before these can be used inside stored procedures, user defined functions, triggers, and user defined data types.</span></span> <span data-ttu-id="22edb-106">SMO は、<xref:Microsoft.SqlServer.Management.Smo.SqlAssembly> オブジェクトを使用してこの機能をサポートします。</span><span class="sxs-lookup"><span data-stu-id="22edb-106">SMO supports this feature with the <xref:Microsoft.SqlServer.Management.Smo.SqlAssembly> object.</span></span>  
  
 <span data-ttu-id="22edb-107"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> オブジェクトは、<xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.AssemblyName%2A> プロパティ、<xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.ClassName%2A> プロパティ、および <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.MethodName%2A> プロパティを使用して .NET アセンブリを参照します。</span><span class="sxs-lookup"><span data-stu-id="22edb-107">The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> object references the .NET assembly with the <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.AssemblyName%2A>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.ClassName%2A>, and <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.MethodName%2A> properties.</span></span>  
  
 <span data-ttu-id="22edb-108"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> オブジェクトが .NET アセンブリを参照する場合、<xref:Microsoft.SqlServer.Management.Smo.SqlAssembly> オブジェクトを作成し、それを <xref:Microsoft.SqlServer.Management.Smo.SqlAssemblyCollection> オブジェクトに属する <xref:Microsoft.SqlServer.Management.Smo.Database> オブジェクトに追加することによって、アセンブリを登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="22edb-108">When the <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> object references a .NET assembly, you must register the assembly by creating a <xref:Microsoft.SqlServer.Management.Smo.SqlAssembly> object and adding it to the <xref:Microsoft.SqlServer.Management.Smo.SqlAssemblyCollection> object, which belongs to the <xref:Microsoft.SqlServer.Management.Smo.Database> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22edb-109">例</span><span class="sxs-lookup"><span data-stu-id="22edb-109">Example</span></span>  
 <span data-ttu-id="22edb-110">提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="22edb-110">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="22edb-111">詳細については、「 [Visual studio .net で VISUAL BASIC SMO プロジェクトを作成する](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)」または「visual [Studio .Net で VISUAL C&#35; Smo プロジェクトを作成](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22edb-111">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-a-scalar-user-defined-function-in-visual-basic"></a><span data-ttu-id="22edb-112">Visual Basic でのユーザー定義スカラー関数の作成</span><span class="sxs-lookup"><span data-stu-id="22edb-112">Creating a Scalar User-Defined Function in Visual Basic</span></span>  
 <span data-ttu-id="22edb-113">このコード例は、入力の <xref:System.DateTime> オブジェクト パラメーターおよび整数型の戻り値を持つユーザー定義のスカラー関数を [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] で作成および削除する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="22edb-113">This code example shows how to create and remove a scalar user-defined function that has an input <xref:System.DateTime> object parameter and an integer return type in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)].</span></span> <span data-ttu-id="22edb-114">ユーザー定義関数は [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] データベースに作成されます。</span><span class="sxs-lookup"><span data-stu-id="22edb-114">The user-defined function is created on the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="22edb-115">この例では、日付引数を取得して ISO 週番号を計算するユーザー定義関数 ISOweek が作成されます。</span><span class="sxs-lookup"><span data-stu-id="22edb-115">The example creates a user-defined function, ISOweek, which takes a date argument and calculates the ISO week number.</span></span> <span data-ttu-id="22edb-116">この関数で正しい計算を行うためには、関数を呼び出す前に、データベースの DATEFIRST オプションが 1 に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="22edb-116">For this function to calculate correctly, the database DATEFIRST option must be set to 1 before the function is called.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBUserDefFuncs1](SMO How to#SMO_VBUserDefFuncs1)]  -->  
  
## <a name="creating-a-scalar-user-defined-function-in-visual-c"></a><span data-ttu-id="22edb-117">Visual C# でのユーザー定義スカラー関数の作成</span><span class="sxs-lookup"><span data-stu-id="22edb-117">Creating a Scalar User-Defined Function in Visual C#</span></span>  
 <span data-ttu-id="22edb-118">このコード例は、入力の <xref:System.DateTime> オブジェクト パラメーターおよび整数型の戻り値を持つユーザー定義のスカラー関数を [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] で作成および削除する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="22edb-118">This code example shows how to create and remove a scalar user-defined function that has an input <xref:System.DateTime> object parameter and an integer return type in [!INCLUDE[csprcs](../../../includes/csprcs-md.md)].</span></span> <span data-ttu-id="22edb-119">ユーザー定義関数は [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] データベースに作成されます。</span><span class="sxs-lookup"><span data-stu-id="22edb-119">The user-defined function is created on the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="22edb-120">この例では、次のユーザー定義関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="22edb-120">The example creates the user-defined function.</span></span> <span data-ttu-id="22edb-121">`ISOweek`.</span><span class="sxs-lookup"><span data-stu-id="22edb-121">`ISOweek`.</span></span> <span data-ttu-id="22edb-122">この関数は、日付引数を受け取って、ISO 週番号を計算します。</span><span class="sxs-lookup"><span data-stu-id="22edb-122">This function takes a date argument and calculates the ISO week number.</span></span> <span data-ttu-id="22edb-123">この関数で正しい計算を行うためには、関数を呼び出す前に、データベースの `DATEFIRST` オプションが `1` に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="22edb-123">For this function to calculate correctly, the database `DATEFIRST` option must be set to `1` before the function is called.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
           Server srv = new Server();  
            //Reference the AdventureWorks2012 database.   
           Database db = srv.Databases["AdventureWorks2012"];  
  
            //Define a UserDefinedFunction object variable by supplying the parent database and the name arguments in the constructor.   
            UserDefinedFunction udf = new UserDefinedFunction(db, "IsOWeek");  
  
            //Set the TextMode property to false and then set the other properties.   
            udf.TextMode = false;  
            udf.DataType = DataType.Int;  
            udf.ExecutionContext = ExecutionContext.Caller;  
            udf.FunctionType = UserDefinedFunctionType.Scalar;  
            udf.ImplementationType = ImplementationType.TransactSql;  
  
            //Add a parameter.   
  
     UserDefinedFunctionParameter par = new UserDefinedFunctionParameter(udf, "@DATE", DataType.DateTime);  
            udf.Parameters.Add(par);  
  
            //Set the TextBody property to define the user-defined function.   
            udf.TextBody = "BEGIN DECLARE @ISOweek int SET @ISOweek= DATEPART(wk,@DATE)+1 -DATEPART(wk,CAST(DATEPART(yy,@DATE) as CHAR(4))+'0104') IF (@ISOweek=0) SET @ISOweek=dbo.ISOweek(CAST(DATEPART(yy,@DATE)-1 AS CHAR(4))+'12'+ CAST(24+DATEPART(DAY,@DATE) AS CHAR(2)))+1 IF ((DATEPART(mm,@DATE)=12) AND ((DATEPART(dd,@DATE)-DATEPART(dw,@DATE))>= 28)) SET @ISOweek=1 RETURN(@ISOweek) END;";  
  
            //Create the user-defined function on the instance of SQL Server.   
            udf.Create();  
  
            //Remove the user-defined function.   
            udf.Drop();  
        }  
```  
  
## <a name="creating-a-scalar-user-defined-function-in-powershell"></a><span data-ttu-id="22edb-124">PowerShell でのユーザー定義スカラー関数の作成</span><span class="sxs-lookup"><span data-stu-id="22edb-124">Creating a Scalar User-Defined Function in PowerShell</span></span>  
 <span data-ttu-id="22edb-125">このコード例は、入力の <xref:System.DateTime> オブジェクト パラメーターおよび整数型の戻り値を持つユーザー定義のスカラー関数を [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] で作成および削除する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="22edb-125">This code example shows how to create and remove a scalar user-defined function that has an input <xref:System.DateTime> object parameter and an integer return type in [!INCLUDE[csprcs](../../../includes/csprcs-md.md)].</span></span> <span data-ttu-id="22edb-126">ユーザー定義関数は [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] データベースに作成されます。</span><span class="sxs-lookup"><span data-stu-id="22edb-126">The user-defined function is created on the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="22edb-127">この例では、次のユーザー定義関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="22edb-127">The example creates the user-defined function.</span></span> <span data-ttu-id="22edb-128">`ISOweek`.</span><span class="sxs-lookup"><span data-stu-id="22edb-128">`ISOweek`.</span></span> <span data-ttu-id="22edb-129">この関数は、日付引数を受け取って、ISO 週番号を計算します。</span><span class="sxs-lookup"><span data-stu-id="22edb-129">This function takes a date argument and calculates the ISO week number.</span></span> <span data-ttu-id="22edb-130">この関数で正しい計算を行うためには、関数を呼び出す前に、データベースの `DATEFIRST` オプションが `1` に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="22edb-130">For this function to calculate correctly, the database `DATEFIRST` option must be set to `1` before the function is called.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
# Define a user defined function object variable by supplying the parent database and name arguments in the constructor.
$udf  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedFunction -argumentlist $db, "IsOWeek"  
  
# Set the TextMode property to false and then set the other properties.
$udf.TextMode = $false  
$udf.DataType = [Microsoft.SqlServer.Management.SMO.DataType]::Int
$udf.ExecutionContext = [Microsoft.SqlServer.Management.SMO.ExecutionContext]::Caller  
$udf.FunctionType = [Microsoft.SqlServer.Management.SMO.UserDefinedFunctionType]::Scalar  
$udf.ImplementationType = [Microsoft.SqlServer.Management.SMO.ImplementationType]::TransactSql  
  
# Define a Parameter object variable by supplying the parent function, name and type arguments in the constructor.  
$type = [Microsoft.SqlServer.Management.SMO.DataType]::DateTime  
$par  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedFunctionParameter -argumentlist $udf, "@DATE",$type  
  
# Add the parameter to the function  
$udf.Parameters.Add($par)  
  
#Set the TextBody property to define the user-defined function.
$udf.TextBody = "BEGIN DECLARE @ISOweek int SET @ISOweek= DATEPART(wk,@DATE)+1 -DATEPART(wk,CAST(DATEPART(yy,@DATE) as CHAR(4))+'0104') IF (@ISOweek=0) SET @ISOweek=dbo.ISOweek(CAST(DATEPART(yy,@DATE)-1 AS CHAR(4))+'12'+ CAST(24+DATEPART(DAY,@DATE) AS CHAR(2)))+1 IF ((DATEPART(mm,@DATE)=12) AND ((DATEPART(dd,@DATE)-DATEPART(dw,@DATE))>= 28)) SET @ISOweek=1 RETURN(@ISOweek) END;"  
  
# Create the user-defined function on the instance of SQL Server.
$udf.Create()  
  
# Remove the user-defined function.
$udf.Drop()  
```  
  
## <a name="see-also"></a><span data-ttu-id="22edb-131">参照</span><span class="sxs-lookup"><span data-stu-id="22edb-131">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction>  

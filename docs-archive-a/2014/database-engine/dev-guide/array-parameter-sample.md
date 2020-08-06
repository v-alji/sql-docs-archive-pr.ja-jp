---
title: 配列パラメーターのサンプル |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: 5d7034ca-ce88-4a7e-8dd9-82f867479e7f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b9afbf13c3797239d142642d9dc6e9ddf9690472
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716713"
---
# <a name="array-parameter-sample"></a><span data-ttu-id="a7de1-102">Array パラメーター サンプル</span><span class="sxs-lookup"><span data-stu-id="a7de1-102">Array Parameter Sample</span></span>
  <span data-ttu-id="a7de1-103">データベース内の行のセットを作成、更新、または削除すると便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="a7de1-103">Sometimes it is useful to create, update, or delete a set of rows in a database.</span></span> <span data-ttu-id="a7de1-104">これを行うには、いくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="a7de1-104">There are several approaches you could use to achieve that goal.</span></span> <span data-ttu-id="a7de1-105">1 つは、共通言語ランタイム (CLR) 統合ユーザー定義データ型を使用して、情報の配列をクライアントからサーバー上の CLR 統合ストアド プロシージャへ渡す方法です。</span><span class="sxs-lookup"><span data-stu-id="a7de1-105">One of them is to pass an array of information from a client to a common language runtime (CLR) integration stored procedure on the server by using a CLR integration user-defined data type.</span></span> <span data-ttu-id="a7de1-106">CLR 統合ユーザー定義データ型の性質によって、サーバーに提供されるデータの大きさは 8,000 バイトに制限されます。</span><span class="sxs-lookup"><span data-stu-id="a7de1-106">The nature of such user-defined data types limits the size of the data provided to the server to 8000 bytes.</span></span> <span data-ttu-id="a7de1-107">したがって、この方法は、大規模なデータや複雑なデータを扱う場合には適切ではありません。</span><span class="sxs-lookup"><span data-stu-id="a7de1-107">Therefore, this approach is not satisfactory for large or complex data.</span></span> <span data-ttu-id="a7de1-108">操作するデータが小規模で単純な場合、この方法は、行ごとにストアド プロシージャを呼び出す方法よりもはるかに効率的です。</span><span class="sxs-lookup"><span data-stu-id="a7de1-108">If the data that is being manipulated is small and simple, this approach can be much more efficient than calling a stored procedure for each row.</span></span> <span data-ttu-id="a7de1-109">データの順序が重要なアプリケーションでは、配列を渡すことでデータの順序を保持できます。このサンプルの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a7de1-109">By passing an array, the order of data is preserved for those applications where the order is significant.This sample contains the following:</span></span>  
  
1.  <span data-ttu-id="a7de1-110">`ContactTypeNames` ユーザー定義データ型。</span><span class="sxs-lookup"><span data-stu-id="a7de1-110">The `ContactTypeNames` user-defined data type.</span></span> <span data-ttu-id="a7de1-111">これには、目的の連絡先の型名のリストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a7de1-111">This contains a list of desired contact type names.</span></span>  
  
2.  <span data-ttu-id="a7de1-112">Microsoft Visual C# または Microsoft Visual Basic メソッドとして実装される `usp_EnsureContactTypeNames`ストアド プロシージャ。</span><span class="sxs-lookup"><span data-stu-id="a7de1-112">The `usp_EnsureContactTypeNames` stored procedure implemented as a Microsoft Visual C# or Microsoft Visual Basic method.</span></span> <span data-ttu-id="a7de1-113">このストアド プロシージャは、`ContactTypeNames` ユーザー定義データ型のインスタンスを受け取り、`Person.ContactType` テーブルにない連絡先名がこのユーザー定義データ型インスタンスに含まれている場合、新しい行をテーブルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="a7de1-113">This accepts an instance of the `ContactTypeNames` user-defined data type and inserts new rows in the `Person.ContactType` table for any contact names that are contained in the user-defined data type instance which are not already present in the table.</span></span>  
  
3.  <span data-ttu-id="a7de1-114">`TestArrayParameter` コンソール アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="a7de1-114">The `TestArrayParameter` console application.</span></span> <span data-ttu-id="a7de1-115">このアプリケーションは、渡されたコマンド ライン パラメーターに基づいて `ContactTypeNames` ユーザー定義データ型のインスタンスを作成し、`usp_EnsureContactTypeNames` ストアド プロシージャを呼び出して、このユーザー定義データ型インスタンスをパラメーターとして渡します。</span><span class="sxs-lookup"><span data-stu-id="a7de1-115">This creates an instance of the `ContactTypeNames` user-defined data type based on the command line parameters passed in, and then invokes the `usp_EnsureContactTypeNames` stored procedure by passing the user-defined data type instance as a parameter.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a7de1-116">前提条件</span><span class="sxs-lookup"><span data-stu-id="a7de1-116">Prerequisites</span></span>  
 <span data-ttu-id="a7de1-117">このプロジェクトを作成して実行するには、次のソフトウェアがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7de1-117">To create and run this project the following the following software must be installed:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a7de1-118">または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express。</span><span class="sxs-lookup"><span data-stu-id="a7de1-118">or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express.</span></span> <span data-ttu-id="a7de1-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express ドキュメントとサンプルの [Web サイト](https://www.microsoft.com/download/details.aspx?id=42299)から無償で入手できます。</span><span class="sxs-lookup"><span data-stu-id="a7de1-119">You can obtain [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express free of charge from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express Documentation and Samples [Web site](https://www.microsoft.com/download/details.aspx?id=42299)</span></span>  
  
-   <span data-ttu-id="a7de1-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] デベロッパー [Web サイト](https://archive.codeplex.com/?p=SqlServerSamples)から入手できる AdventureWorks データベース。</span><span class="sxs-lookup"><span data-stu-id="a7de1-120">The AdventureWorks database that is available at the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Developer [Web site](https://archive.codeplex.com/?p=SqlServerSamples)</span></span>  
  
-   <span data-ttu-id="a7de1-121">.NET Framework SDK 2.0 以降または Microsoft Visual Studio 2005 以降。</span><span class="sxs-lookup"><span data-stu-id="a7de1-121">.NET Framework SDK 2.0 or later or Microsoft Visual Studio 2005 or later.</span></span> <span data-ttu-id="a7de1-122">.NET Framework SDK は無償で入手できます。</span><span class="sxs-lookup"><span data-stu-id="a7de1-122">You can obtain .NET Framework SDK free of charge.</span></span>  
  
-   <span data-ttu-id="a7de1-123">また、次の条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7de1-123">In addition, the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="a7de1-124">使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスで CLR 統合が有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7de1-124">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using must have CLR integration enabled.</span></span>  
  
-   <span data-ttu-id="a7de1-125">CLR 統合を有効にするには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="a7de1-125">In order to enable CLR integration, perform the following steps:</span></span>  
  
    #### <a name="enabling-clr-integration"></a><span data-ttu-id="a7de1-126">CLR 統合の有効化</span><span class="sxs-lookup"><span data-stu-id="a7de1-126">Enabling CLR Integration</span></span>  
  
    -   <span data-ttu-id="a7de1-127">以下の [!INCLUDE[tsql](../../includes/tsql-md.md)] コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="a7de1-127">Execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] commands:</span></span>  
  
     `sp_configure 'clr enabled', 1`  
  
     `GO`  
  
     `RECONFIGURE`  
  
     `GO`  
  
    > [!NOTE]  
    >  <span data-ttu-id="a7de1-128">CLR を有効にするには、 `ALTER SETTINGS` サーバーレベルの権限が必要です。この権限は、 `sysadmin` 固定サーバーロールおよびのメンバーによって暗黙的に保持されてい `serveradmin` ます。</span><span class="sxs-lookup"><span data-stu-id="a7de1-128">To enable CLR, you must have `ALTER SETTINGS` server level permission, which is implicitly held by members of the `sysadmin` and `serveradmin` fixed server roles.</span></span>  
  
-   <span data-ttu-id="a7de1-129">使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに AdventureWorks データベースがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7de1-129">The AdventureWorks database must be installed on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using.</span></span>  
  
-   <span data-ttu-id="a7de1-130">使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの管理者でない場合は、インストールを完了するために **CreateAssembly** 権限が管理者から付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7de1-130">If you are not an administrator for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using, you must have an administrator grant you **CreateAssembly**  permission to complete the installation.</span></span>  
  
## <a name="building-the-sample"></a><span data-ttu-id="a7de1-131">サンプルのビルド</span><span class="sxs-lookup"><span data-stu-id="a7de1-131">Building the Sample</span></span>  
  
#### <a name="create-and-run-the-sample-by-using-the-following-instructions"></a><span data-ttu-id="a7de1-132">次の手順に従ってサンプルを作成し、実行します。</span><span class="sxs-lookup"><span data-stu-id="a7de1-132">Create and run the sample by using the following instructions:</span></span>  
  
1.  <span data-ttu-id="a7de1-133">Visual Studio または .NET Framework のコマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="a7de1-133">Open a Visual Studio or .NET Framework command prompt.</span></span>  
  
2.  <span data-ttu-id="a7de1-134">必要な場合は、サンプル用のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="a7de1-134">If necessary, create a directory for your sample.</span></span> <span data-ttu-id="a7de1-135">この例では C:\MySample を使用します。</span><span class="sxs-lookup"><span data-stu-id="a7de1-135">For this example, we will use C:\MySample.</span></span>  
  
3.  <span data-ttu-id="a7de1-136">c:\MySample で、`ContactTypeNames.vb` (Visual Basic サンプル) または `ContactTypeNames.cs` (C# サンプル) を作成し、適切な Visual Basic または C# のサンプル コード (下記) をこのファイルにコピーします。</span><span class="sxs-lookup"><span data-stu-id="a7de1-136">In c:\MySample, create `ContactTypeNames.vb` (for the Visual Basic sample) or `ContactTypeNames.cs` (for the C# sample) and copy the appropriate Visual Basic or C# sample code (below) into the file.</span></span>  
  
4.  <span data-ttu-id="a7de1-137">選択した言語に応じて次のいずれかをコマンド プロンプトで実行し、サンプル コードを必要なアセンブリにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="a7de1-137">Compile the sample code into the required assembly from the command line prompt by executing one of the following, depending on your choice of language.</span></span>  
  
    -   `Vbc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Xml.dll  /target:library ContactTypeNames.vb`  
  
    -   `Csc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Xml.dll /target:library ContactTypeNames.cs`  
  
5.  <span data-ttu-id="a7de1-138">c:\MySample で、`Program.vb` (Visual Basic サンプル) または `Program.cs` (C# サンプル) を作成し、適切な Visual Basic または C# のサンプル コード (下記) をこのファイルにコピーします。</span><span class="sxs-lookup"><span data-stu-id="a7de1-138">In c:\MySample, create `Program.vb` (for the Visual Basic sample) or `Program.cs` (for the C# sample) and copy the appropriate Visual Basic or C# sample code (below) into the file.</span></span>  
  
6.  <span data-ttu-id="a7de1-139">ファイルプログラム内の適切な行 (24 行目) を探し、を `XXX` のインスタンスの名前に置き換えます。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7de1-139">Locate the appropriate line in the file Program (around line 24) and replace `XXX` with the name of your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
    -   `Dim connection As New SqlConnection("data source=XXX;initial catalog=AdventureWorks;Integrated Security=SSPI")`  
  
    -   `using (SqlConnection connection = new SqlConnection("data source=XXX;initial catalog=AdventureWorks;Integrated Security=SSPI"))`  
  
7.  <span data-ttu-id="a7de1-140">選択した言語に応じて次のいずれかをコマンド プロンプトで実行し、サンプル コードを必要な実行可能ファイルにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="a7de1-140">Compile the sample code into the required executable from the command line prompt by executing one of the following, depending on your choice of language.</span></span>  
  
    -   `vbc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Deployment.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Drawing.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Windows.Forms.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Xml.dll,C:\MySample\ContactTypeNames.dll /out:TestArrayParameter Program.vb`  
  
    -   `Csc /reference:ContactTypeNames.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Xml.dll /out:TestArrayParameter.exe Program.cs`  
  
8.  <span data-ttu-id="a7de1-141">[!INCLUDE[tsql](../../includes/tsql-md.md)] インストール コードをファイルにコピーし、`Install.sql` としてサンプル ディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="a7de1-141">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation code into a file and save it as `Install.sql` in the sample directory.</span></span>  
  
9. <span data-ttu-id="a7de1-142">サンプルが `C:\MySample\`以外のディレクトリにインストールされている場合は、その場所を示すように、ファイル `Install.sql` を編集します。</span><span class="sxs-lookup"><span data-stu-id="a7de1-142">If the sample is installed in a directory other then `C:\MySample\`, edit the file `Install.sql` as indicated to point to that location.</span></span>  
  
10. <span data-ttu-id="a7de1-143">次のコマンドを実行して、アセンブリ、ストアド プロシージャ、および関数を配置します。</span><span class="sxs-lookup"><span data-stu-id="a7de1-143">Deploy the assembly, stored procedure and functions by executing</span></span>  
  
    -   `sqlcmd -E -I -i install.sql`  
  
11. <span data-ttu-id="a7de1-144">次のコマンドをコマンド プロンプトで実行して、アプリケーションをテストします。</span><span class="sxs-lookup"><span data-stu-id="a7de1-144">Test the application by executing the following line at the command prompt:</span></span>  
  
    -   `TestArrayParameter "Executive Sales Representative" "Executive Sales Manager"`  
  
12. <span data-ttu-id="a7de1-145">[!INCLUDE[tsql](../../includes/tsql-md.md)] クリーンアップ スクリプトをファイルにコピーし、`cleanup.sql` としてサンプル ディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="a7de1-145">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] cleanup script into a file and save it as `cleanup.sql` in the sample directory.</span></span>  
  
13. <span data-ttu-id="a7de1-146">次のコマンドを使用してこのスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="a7de1-146">Execute the script with the  following command</span></span>  
  
    -   `sqlcmd -E -I -i cleanup.sql`  
  
## <a name="sample-code"></a><span data-ttu-id="a7de1-147">サンプル コード</span><span class="sxs-lookup"><span data-stu-id="a7de1-147">Sample Code</span></span>  
 <span data-ttu-id="a7de1-148">このサンプルのコード リストを次に示します。</span><span class="sxs-lookup"><span data-stu-id="a7de1-148">The following are the code listings for this sample.</span></span>  
  
 <span data-ttu-id="a7de1-149">次に示すのは、ライブラリ `ContactTypeNames.` のコードです。</span><span class="sxs-lookup"><span data-stu-id="a7de1-149">This is the code for the Library `ContactTypeNames.`</span></span>  
  
 <span data-ttu-id="a7de1-150">C#</span><span class="sxs-lookup"><span data-stu-id="a7de1-150">C#</span></span>  
  
```  
#region Using directives  
  
using System;  
using System.Data;  
using System.Data.Sql;  
using System.Data.SqlTypes;  
using System.Collections;  
using System.Collections.Generic;  
using System.Text;  
using System.Globalization;  
using Microsoft.SqlServer.Server;  
  
#endregion  
  
    // This class is used to demonstrate passing an array of a fairly small number of reasonably small strings  
    // to a CLR integration based stored procedure on the server.  Because a UDT is limited to 8000 bytes  
    // this approach will not work well for large numbers of strings or long strings.  See the contact  
    // creation stored procedure in the AdventureWorks CLR integration sample for an alternative approach  
    // using XML which does not have these limitations.  
    [Serializable]  
    [Microsoft.SqlServer.Server.SqlUserDefinedType(Microsoft.SqlServer.Server.Format.UserDefined, IsByteOrdered = true, MaxByteSize = 8000)]  
    public class ContactTypeNames : INullable, Microsoft.SqlServer.Server.IBinarySerialize  
    {  
  
        #region Constructors  
        private const int maxByteSize = 8000;  
  
        public ContactTypeNames()  
        {  
        }  
  
        public ContactTypeNames(string[] names)  
        {  
            int numberOfCharacters = 0;  
            foreach (string name in names)  
            {  
                if (name.Length == 0)   
                    throw new ArgumentException("Zero length names are not allowed");  
                numberOfCharacters += name.Length;  
            }  
            int dataByteSize = numberOfCharacters*2 //UTF-16 characters take 2 bytes  
                + names.Length*4  //Four byte header for each string  
                + 4                 //Four byte header for null string at end  
                + 1;                //One byte boolean for null flag  
            if (dataByteSize >= maxByteSize)  
                throw new ArgumentException(string.Format(CultureInfo.InvariantCulture, "Data provided occupies {0} bytes but only {1} bytes "  
                    + "are available", dataByteSize, maxByteSize));  
  
            this._names = names;  
        }  
        #endregion  
  
        #region Accessors  
        public string[] GetTypeNameArray()  
        {  
            //Don't let caller modify our copy of the array  
            return (string[])_names.Clone();  
        }  
  
        //This has an odd API because we can only define Transact-SQL functions on static methods.  
        [SqlFunctionAttribute(FillRowMethodName = "FillNameRow")]  
        public static IEnumerable GetContactTypeNames(ContactTypeNames names)  
        {  
            if (names == null)  
                throw new ArgumentNullException("names");  
  
            return names.GetTypeNameArray();  
        }  
  
        public static void FillNameRow(object nameArrayElement, out string contactName)  
        {  
            contactName = (string)nameArrayElement;  
        }  
  
        #endregion  
  
        #region String Conversions  
  
        /// <summary>  
        /// The string format for contact type names is a sequence of names separated by commas  
        /// </summary>  
        /// <param name="s">a string containing contact type names separated by commas</param>  
        /// <returns>An instance of contact type name containing the specified names</returns>  
        [Microsoft.SqlServer.Server.SqlMethod(DataAccess = Microsoft.SqlServer.Server.DataAccessKind.None, IsDeterministic = false, IsMutator = false, IsPrecise = false,  
        SystemDataAccess = Microsoft.SqlServer.Server.SystemDataAccessKind.None)]  
        public static ContactTypeNames Parse(SqlString s)  
        {  
            if (s.IsNull)  
                return Null;  
            return new ContactTypeNames(s.Value.Split(new char[] {','}));  
        }  
  
        /// <summary>  
        /// Convert the contact type names to a string  
        /// </summary>  
        /// <returns>The contact type names separated by commas</returns>  
        public override string ToString()  
        {  
            if (this.IsNull)  
                return null;  
  
            StringBuilder sb = new StringBuilder();  
            foreach (string name in _names)  
            {  
                if (sb.Length > 0) sb.Append(", ");  
                sb.Append(name);  
            }  
  
            return sb.ToString();  
        }  
        #endregion  
  
        #region INullable Members  
  
        public static ContactTypeNames Null  
        {  
            get  
            {  
                return new ContactTypeNames();  
            }  
        }  
        public bool IsNull  
        {  
            get   
            {   
                return _names == null;   
            }  
        }  
  
        #endregion  
  
        #region IBinarySerialize Members  
  
        //Format:   
        //Byte 1: Null flag (boolean) (true = null)  
        //Byte 2 - 7994: Strings with 4 byte length headers,  
        //               last string is a zero length string.  
        //This format is in part dictated by how the BinaryWriter serializes strings.  See  
        //the Microsoft .NET Framework documentation on System.IO.BinaryWriter for more details.  
  
        public void Read(System.IO.BinaryReader r)  
        {  
            if (r.ReadBoolean())  
            {  
                _names = null;  
                return;  
            }  
            List<String> nameList = new List<String>();  
            string name;  
            while ((name = r.ReadString()).Length != 0)  
            {  
                nameList.Add(name);  
            }  
            _names = new string[nameList.Count];  
            nameList.CopyTo(_names);  
        }  
  
        public void Write(System.IO.BinaryWriter w)  
        {  
            if (w == null)  
                throw new ArgumentNullException("w");  
  
            w.Write(this.IsNull);  
            foreach (string name in _names)  
            {  
                w.Write(name);  
            }  
            w.Write(string.Empty);              
        }  
  
        #endregion  
  
        #region Private Implementation  
  
        private string[] _names;  
        #endregion  
    }  
```  
  
 <span data-ttu-id="a7de1-151">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a7de1-151">Visual Basic</span></span>  
  
```  
#Region "Using directives"  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports System.Collections  
Imports System.Collections.Generic  
Imports System.Text  
Imports System.Globalization  
Imports Microsoft.SqlServer.Server  
Imports System.Runtime.InteropServices  
#End Region  
  
' This class is used to demonstrate passing an array of a fairly small number of reasonably small strings  
' to a CLR integration based stored procedure on the server.  Because a UDT is limited to 8000 bytes  
' this approach will not work well for large numbers of strings or long strings.  See the contact  
' creation stored procedure in the AdventureWorks CLR integration sample for an alternative approach  
' using XML which does not have these limitations.  
<Serializable()> _  
<SqlUserDefinedType(Format.UserDefined, IsByteOrdered:=True, maxByteSize:=8000), CLSCompliant(False)> _  
Public Class ContactTypeNames  
    Implements INullable, IBinarySerialize  
  
#Region "Constructors"  
    Private Const maxByteSize As Integer = 8000  
  
    Public Sub New()  
    End Sub  
  
    Public Sub New(ByVal names() As String)  
        Dim numberOfCharacters As Integer = 0  
  
        For Each name As String In names  
            If name.Length = 0 Then  
                Throw New ArgumentException("Zero length names are not allowed")  
            End If  
  
            numberOfCharacters += name.Length  
        Next  
  
        'UTF-16 characters take 2 bytes  
        'Four byte header for each string  
        'Four byte header for null string at end  
        'One byte boolean for null flag  
        Dim dataByteSize As Integer = numberOfCharacters * 2 _  
            + names.Length * 4 _  
            + 4 _  
            + 1  
  
        If dataByteSize >= maxByteSize Then  
            Throw New ArgumentException(String.Format(CultureInfo.InvariantCulture, _  
                "Data provided occupies {0} bytes but only {1} bytes are available", _  
                dataByteSize, maxByteSize))  
        End If  
  
        Me._names = names  
    End Sub  
#End Region  
  
#Region "Accessors"  
  
    Public Function GetTypeNameArray() As String()  
        'Don't let caller modify our copy of the array  
        Return CType(Me._names.Clone(), String())  
    End Function  
  
    'This has an odd API because we can only define Transact-SQL functions on static methods.  
    <SqlFunction(FillRowMethodName:="FillNameRow", TableDefinition:="[Name] [Name]")> _  
    Public Shared Function GetContactTypeNames(ByVal names As ContactTypeNames) As IEnumerable  
        If names Is Nothing Then  
            Throw New ArgumentNullException("names")  
        End If  
  
        Return names.GetTypeNameArray()  
    End Function  
  
    Public Shared Sub FillNameRow(ByVal nameArrayElement As Object, <Out()> ByRef contactName As String)  
        contactName = CStr(nameArrayElement)  
    End Sub  
  
#End Region  
  
#Region "String Conversions"  
  
    ''' <summary>  
    ''' The string format for contact type names is a sequence of names separated by commas  
    ''' </summary>  
    ''' <param name="s">a string containing contact type names separated by commas</param>  
    ''' <returns>An instance of contact type name containing the specified names</returns>  
    <Microsoft.SqlServer.Server.SqlMethod(DataAccess:=Microsoft.SqlServer.Server.DataAccessKind.None, IsDeterministic:=False, IsMutator:=False, IsPrecise:=False, SystemDataAccess:=Microsoft.SqlServer.Server.SystemDataAccessKind.None)> _  
    Public Shared Function Parse(ByVal s As SqlString) As ContactTypeNames  
        If s.IsNull Then  
            Return Nothing  
        End If  
  
        Return New ContactTypeNames(s.Value.Split(New Char() {","c}))  
    End Function  
  
    ''' <summary>  
    ''' Convert the contact type names to a string  
    ''' </summary>  
    ''' <returns>The contact type names separated by commas</returns>  
    Public Overrides Function ToString() As String  
        If Me.IsNull Then  
            Return Nothing  
        End If  
  
        Dim sb As New StringBuilder()  
  
        For Each name As String In Me._names  
            If sb.Length > 0 Then  
                sb.Append(", ")  
            End If  
  
            sb.Append(name)  
        Next name  
  
        Return sb.ToString()  
    End Function  
#End Region  
  
#Region "INullable Members"  
  
    Shared ReadOnly Property Null() As ContactTypeNames  
        Get  
            Return New ContactTypeNames()  
        End Get  
    End Property  
  
    Public ReadOnly Property IsNull() As Boolean Implements INullable.IsNull  
        Get  
            Return Me._names Is Nothing  
        End Get  
    End Property  
  
#End Region  
  
#Region "IBinarySerialize Members"  
  
    'Format:   
    'Byte 1: Null flag (boolean) (true = null)  
    'Byte 2 - 7994: Strings with 4 byte length headers,  
    '               last string is a zero length string.  
    'This format is in part dictated by how the BinaryWriter serializes strings.  See  
    'the Microsoft .NET Framework documentation on System.IO.BinaryWriter for more details.  
    Public Sub Read(ByVal r As System.IO.BinaryReader) Implements IBinarySerialize.Read  
        If r.ReadBoolean() Then  
            Me._names = Nothing  
            Return  
        End If  
  
        Dim nameList As New List(Of String)  
        Dim name As String = r.ReadString()  
        While name.Length <> 0  
            nameList.Add(name)  
            name = r.ReadString()  
        End While  
  
        Me._names = New String(nameList.Count - 1) {}  
        nameList.CopyTo(Me._names)  
    End Sub  
  
    Public Sub Write(ByVal w As System.IO.BinaryWriter) Implements IBinarySerialize.Write  
        If w Is Nothing Then  
            Throw New ArgumentNullException("w")  
        End If  
  
        w.Write(Me.IsNull)  
  
        For Each name As String In Me._names  
            w.Write(name)  
        Next  
  
        w.Write(String.Empty)  
    End Sub  
  
#End Region  
  
#Region "Private Implementation"  
    Private _names() As String  
#End Region  
  
End Class  
```  
  
 <span data-ttu-id="a7de1-152">次に示すのは、テスト用の実行可能ファイルのコードです。</span><span class="sxs-lookup"><span data-stu-id="a7de1-152">This is the code for the test executable.</span></span>  
  
 <span data-ttu-id="a7de1-153">C#</span><span class="sxs-lookup"><span data-stu-id="a7de1-153">C#</span></span>  
  
```  
#region Using directives  
  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.IO;  
using System.Data;  
using System.Data.Sql;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
#endregion  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            if (args.Length == 0)  
            {  
                Console.WriteLine("Usage: TestArrayParameter contactTypeName1 "  
                    + "contactTypeName2 ... contactTypeNamen");  
                return;  
            }  
            using (SqlConnection connection = new SqlConnection("data source=XXX;initial catalog=AdventureWorks;Integrated Security=SSPI"))  
            {  
                connection.Open();  
                ShowTypeNames(connection, "before any inserts");  
  
                SqlCommand command = connection.CreateCommand();  
                command.CommandText = "usp_EnsureContactTypeNames";  
                command.CommandType = CommandType.StoredProcedure;  
                SqlParameter namesParameter = new SqlParameter("@names", SqlDbType.Udt);  
                namesParameter.UdtTypeName = "ContactTypeNames";  
                namesParameter.Value = new ContactTypeNames(args);  
                command.Parameters.Add(namesParameter);  
                command.ExecuteNonQuery();  
  
                ShowTypeNames(connection, "after any inserts");  
  
            }  
  
        }  
  
        private static void ShowTypeNames(SqlConnection connection, string whenRan)  
        {  
            SqlCommand command = connection.CreateCommand();  
            command.CommandText = "SELECT Name FROM Person.ContactType ORDER BY Name";  
            using (SqlDataReader reader = command.ExecuteReader())  
            {  
                Console.BackgroundColor = ConsoleColor.Blue;  
                Console.Write("Contact type names {0}: ", whenRan);  
                Console.ResetColor();  
                bool first = true;  
                while (reader.Read())  
                {  
                    if (!first) Console.Write(", ");  
                    Console.Write(reader[0].ToString());  
                    first = false;  
                }  
                Console.WriteLine("");  
                Console.WriteLine("");  
            }  
  
        }  
    }  
```  
  
 <span data-ttu-id="a7de1-154">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a7de1-154">Visual Basic</span></span>  
  
```  
#Region "Using directives"  
Imports System  
Imports System.Collections.Generic  
Imports System.Text  
Imports System.IO  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports System.Data.SqlClient  
#End Region  
  
Class Program  
  
    Shared Sub Main(ByVal args() As String)  
        If args.Length = 0 Then  
            Console.WriteLine("Usage: TestArrayParameter contactTypeName1 " _  
                + "contactTypeName2 ... contactTypeNamen")  
            Return  
        End If  
  
        Dim connection As New SqlConnection("data source=XXX;initial catalog=AdventureWorks;Integrated Security=SSPI")  
        Try  
            connection.Open()  
            ShowTypeNames(connection, "Before any inserts")  
  
            Dim command As SqlCommand = connection.CreateCommand()  
            command.CommandText = "usp_EnsureContactTypeNames"  
            command.CommandType = CommandType.StoredProcedure  
            Dim namesParameter As New SqlParameter("@names", SqlDbType.Udt)  
            namesParameter.UdtTypeName = "ContactTypeNames"  
            namesParameter.Value = New ContactTypeNames(args)  
            command.Parameters.Add(namesParameter)  
            command.ExecuteNonQuery()  
  
            ShowTypeNames(connection, "After any inserts")  
        Finally  
            connection.Dispose()  
        End Try  
    End Sub  
  
    Private Shared Sub ShowTypeNames(ByVal connection As SqlConnection, ByVal whenRan As String)  
        Dim command As SqlCommand = connection.CreateCommand()  
        command.CommandText = "SELECT [Name] FROM [Person].[ContactType] ORDER BY Name"  
        Dim reader As SqlDataReader = command.ExecuteReader()  
        Try  
            Console.BackgroundColor = ConsoleColor.Blue  
            Console.Write("Contact type names {0}: ", whenRan)  
            Console.ResetColor()  
            Dim first As Boolean = True  
            While reader.Read()  
                If Not first Then  
                    Console.Write(", ")  
                End If  
  
                Console.Write(reader(0).ToString())  
                first = False  
            End While  
  
            Console.WriteLine("")  
            Console.WriteLine("")  
        Finally  
            reader.Dispose()  
        End Try  
  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="a7de1-155">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] インストール スクリプト (`Install.sql`) は、アセンブリを配置し、データベースにストアド プロシージャと関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="a7de1-155">This is the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation script (`Install.sql`), which deploys the assembly and creates the stored procedure and functions in the database.</span></span>  
  
```  
USE AdventureWorks  
GO  
  
-- Drop existing sprocs, type, and assemblies if any.  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_EnsureContactTypeNames')  
DROP PROCEDURE usp_EnsureContactTypeNames;  
GO  
  
IF EXISTS (SELECT * FROM sys.objects WHERE [name] = N'GetContactTypeNames' and (type = 'FS' or type = 'FT'))    
DROP FUNCTION [GetContactTypeNames];  
GO  
  
IF EXISTS (SELECT * FROM sys.types WHERE [name] = 'ContactTypeNames')  
DROP TYPE ContactTypeNames;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'ContactTypeNames')  
DROP ASSEMBLY ContactTypeNames;  
GO  
  
-- Add assemblies, type, and sproc  
  
DECLARE @SamplesPath nvarchar(1024)  
-- You may need to modify the value of the this variable if you have installed the sample someplace other than the default location.  
set @SamplesPath= 'C:\MySample\'  
CREATE ASSEMBLY ContactTypeNames   
FROM @SamplesPath + 'ContactTypeNames.dll'  
WITH permission_set = Safe;  
  
CREATE TYPE ContactTypeNames  
EXTERNAL NAME ContactTypeNames.ContactTypeNames;  
GO  
  
CREATE FUNCTION GetContactTypeNames  
(  
@names dbo.ContactTypeNames  
)  
RETURNS TABLE  
(  
[Name] [Name]  
)  
AS EXTERNAL NAME [ContactTypeNames].[ContactTypeNames].[GetContactTypeNames];  
GO  
  
CREATE PROCEDURE usp_EnsureContactTypeNames  
(  
@names dbo.ContactTypeNames  
)  
AS  
SET NOCOUNT ON;  
  
INSERT Person.ContactType ([Name])  
SELECT [Name] FROM GetContactTypeNames(@names) AS PotentialNames  
WHERE [Name] NOT IN (SELECT [Name] FROM Person.ContactType);   
GO  
```  
  
 <span data-ttu-id="a7de1-156">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] は、データベースからアセンブリとストアド プロシージャを削除します。</span><span class="sxs-lookup"><span data-stu-id="a7de1-156">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] removes the assembly and stored procedure from the database.</span></span>  
  
```  
USE AdventureWorks  
GO  
  
DELETE Person.ContactType WHERE ContactTypeID > 20;  
GO  
  
-- Drop existing sprocs, type, and assemblies if any.  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_EnsureContactTypeNames')  
DROP PROCEDURE usp_EnsureContactTypeNames;  
GO  
  
IF EXISTS (SELECT * FROM sys.objects WHERE [name] = N'GetContactTypeNames' and (type = 'FS' or type = 'FT'))    
DROP FUNCTION [GetContactTypeNames];  
GO  
  
IF EXISTS (SELECT * FROM sys.types WHERE [name] = 'ContactTypeNames')  
DROP TYPE ContactTypeNames;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'ContactTypeNames')  
DROP ASSEMBLY ContactTypeNames;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7de1-157">参照</span><span class="sxs-lookup"><span data-stu-id="a7de1-157">See Also</span></span>  
 [<span data-ttu-id="a7de1-158">CLR &#40;共通言語ランタイム&#41; 統合の使用シナリオと例</span><span class="sxs-lookup"><span data-stu-id="a7de1-158">Usage Scenarios and Examples for Common Language Runtime &#40;CLR&#41; Integration</span></span>](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  

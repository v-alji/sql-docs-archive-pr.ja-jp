---
title: 文字列ユーティリティ関数のサンプル |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: 9623013f-15f1-4614-8dac-1155e57c880c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: c0c5a933952b784fccbe1a5fe20519da333eeb67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716705"
---
# <a name="string-utility-functions-sample"></a><span data-ttu-id="24a87-102">文字列ユーティリティ関数サンプル</span><span class="sxs-lookup"><span data-stu-id="24a87-102">String Utility Functions Sample</span></span>
  <span data-ttu-id="24a87-103">String Utilities サンプルには、Visual C# と Visual Basic で記述されたストリーミング テーブル値関数が含まれています。この関数は、コンマ区切りの文字列を 1 列のテーブルに分割します。</span><span class="sxs-lookup"><span data-stu-id="24a87-103">The String Utilities sample contains a streaming table-valued function written in Visual C# and Visual Basic, which splits a comma-separated string into a table with one column.</span></span> <span data-ttu-id="24a87-104">また、文字列の列をコンマ区切りの文字列に変換する集計関数も含まれています。</span><span class="sxs-lookup"><span data-stu-id="24a87-104">It also contains an aggregate function that converts a string column to a comma-separated string.</span></span>  <span data-ttu-id="24a87-105">さらに、正規表現置換機能と正規表現検索機能を提供するスカラー関数およびテーブル値関数も実装されています。</span><span class="sxs-lookup"><span data-stu-id="24a87-105">Also implemented are a scalar function and a table-valued function that provide regular expression replacement and regular expression searching functionality.</span></span>  
  
 <span data-ttu-id="24a87-106">ストリーミング テーブル値関数を実装するには、`IEnumerable` インターフェイスを実装するオブジェクトを返すメソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="24a87-106">To implement a streaming table-valued function, create a method that returns an object that implements the `IEnumerable` interface.</span></span> <span data-ttu-id="24a87-107">この `IEnumerable` メソッドは、属性によって、テーブル値関数の行を満たす別のメソッドにリンクされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="24a87-107">This `IEnumerable` method must be linked by an attribute to another method which fills in rows of the table-valued function.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="24a87-108">前提条件</span><span class="sxs-lookup"><span data-stu-id="24a87-108">Prerequisites</span></span>  
 <span data-ttu-id="24a87-109">このプロジェクトを作成して実行するには、次のソフトウェアがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="24a87-109">To create and run this project the following the following software must be installed:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="24a87-110">または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express。</span><span class="sxs-lookup"><span data-stu-id="24a87-110">or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express.</span></span> <span data-ttu-id="24a87-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express ドキュメントとサンプルの [Web サイト](https://www.microsoft.com/download/details.aspx?id=42299)から無償で入手できます。</span><span class="sxs-lookup"><span data-stu-id="24a87-111">You can obtain [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express free of charge from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express Documentation and Samples [Web site](https://www.microsoft.com/download/details.aspx?id=42299)</span></span>  
  
-   <span data-ttu-id="24a87-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] デベロッパー [Web サイト](https://archive.codeplex.com/?p=SqlServerSamples)から入手できる AdventureWorks データベース。</span><span class="sxs-lookup"><span data-stu-id="24a87-112">The AdventureWorks database that is available at the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Developer [Web site](https://archive.codeplex.com/?p=SqlServerSamples)</span></span>  
  
-   <span data-ttu-id="24a87-113">.NET Framework SDK 2.0 以降または Microsoft Visual Studio 2005 以降。</span><span class="sxs-lookup"><span data-stu-id="24a87-113">.NET Framework SDK 2.0 or later or Microsoft Visual Studio 2005 or later.</span></span> <span data-ttu-id="24a87-114">.NET Framework SDK は無償で入手できます。</span><span class="sxs-lookup"><span data-stu-id="24a87-114">You can obtain .NET Framework SDK free of charge.</span></span>  
  
-   <span data-ttu-id="24a87-115">また、次の条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="24a87-115">In addition, the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="24a87-116">使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスで CLR 統合が有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="24a87-116">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using must have CLR integration enabled.</span></span>  
  
-   <span data-ttu-id="24a87-117">CLR 統合を有効にするには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="24a87-117">In order to enable CLR integration, perform the following steps:</span></span>  
  
    #### <a name="enabling-clr-integration"></a><span data-ttu-id="24a87-118">CLR 統合の有効化</span><span class="sxs-lookup"><span data-stu-id="24a87-118">Enabling CLR Integration</span></span>  
  
    -   <span data-ttu-id="24a87-119">以下の [!INCLUDE[tsql](../../includes/tsql-md.md)] コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="24a87-119">Execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] commands:</span></span>  
  
     `sp_configure 'clr enabled', 1`  
  
     `GO`  
  
     `RECONFIGURE`  
  
     `GO`  
  
    > [!NOTE]  
    >  <span data-ttu-id="24a87-120">CLR 統合を有効にするには、 `ALTER SETTINGS` サーバーレベルのアクセス許可が必要です。この権限は、 `sysadmin` 固定サーバーロールおよびのメンバーによって暗黙的に保持されてい `serveradmin` ます。</span><span class="sxs-lookup"><span data-stu-id="24a87-120">To enable CLR integration, you must have `ALTER SETTINGS` server level permission, which is implicitly held by members of the `sysadmin` and `serveradmin` fixed server roles.</span></span>  
  
-   <span data-ttu-id="24a87-121">使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに AdventureWorks データベースがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="24a87-121">The AdventureWorks database must be installed on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using.</span></span>  
  
-   <span data-ttu-id="24a87-122">使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの管理者でない場合は、インストールを完了するために **CreateAssembly** 権限が管理者から付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="24a87-122">If you are not an administrator for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using, you must have an administrator grant you **CreateAssembly**  permission to complete the installation.</span></span>  
  
## <a name="building-the-sample"></a><span data-ttu-id="24a87-123">サンプルのビルド</span><span class="sxs-lookup"><span data-stu-id="24a87-123">Building the Sample</span></span>  
  
#### <a name="create-and-run-the-sample-by-using-the-following-instructions"></a><span data-ttu-id="24a87-124">次の手順に従ってサンプルを作成し、実行します。</span><span class="sxs-lookup"><span data-stu-id="24a87-124">Create and run the sample by using the following instructions:</span></span>  
  
1.  <span data-ttu-id="24a87-125">Visual Studio または .NET Framework のコマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="24a87-125">Open a Visual Studio or .NET Framework command prompt.</span></span>  
  
2.  <span data-ttu-id="24a87-126">必要な場合は、サンプル用のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="24a87-126">If necessary, create a directory for your sample.</span></span> <span data-ttu-id="24a87-127">この例では C:\MySample を使用します。</span><span class="sxs-lookup"><span data-stu-id="24a87-127">For this example, we will use C:\MySample.</span></span>  
  
3.  <span data-ttu-id="24a87-128">c:\MySample で、`StringUtils.vb` (Visual Basic サンプル) または `StringUtils.cs` (C# サンプル) を作成し、適切な Visual Basic または C# のサンプル コード (下記) をこのファイルにコピーします。</span><span class="sxs-lookup"><span data-stu-id="24a87-128">In c:\MySample, create `StringUtils.vb` (for the Visual Basic sample) or `StringUtils.cs` (for the C# sample) and copy the appropriate Visual Basic or C# sample code (below) into the file.</span></span>  
  
4.  <span data-ttu-id="24a87-129">選択した言語に応じて次のいずれかをコマンド プロンプトで実行し、サンプル コードをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="24a87-129">Compile the sample code from the command line prompt by executing one of the following, depending on your choice of language.</span></span>  
  
    -   `Vbc /target:library /reference:"C:\Program Files (x86)\Reference Assemblies\Microsoft\Framework\v3.5\System.Core.dll",C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Xml.dll /debug- /target:library StringUtils.vb`  
  
    -   `Csc/reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.XML.dll /target:library StringUtils.cs`  
  
5.  <span data-ttu-id="24a87-130">[!INCLUDE[tsql](../../includes/tsql-md.md)] インストール コードをファイルにコピーし、`Install.sql` としてサンプル ディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="24a87-130">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation code into a file and save it as `Install.sql` in the sample directory.</span></span>  
  
6.  <span data-ttu-id="24a87-131">サンプルが `C:\MySample\`以外のディレクトリにインストールされている場合は、その場所を示すように、ファイル `Install.sql` を編集します。</span><span class="sxs-lookup"><span data-stu-id="24a87-131">If the sample is installed in a directory other then `C:\MySample\`, edit the file `Install.sql` as indicated to point to that location.</span></span>  
  
7.  <span data-ttu-id="24a87-132">次のコマンドを実行して、アセンブリとストアド プロシージャを配置します。</span><span class="sxs-lookup"><span data-stu-id="24a87-132">Deploy the assembly and stored procedure by executing</span></span>  
  
    -   `sqlcmd -E -I -i install.sql`  
  
    -   <span data-ttu-id="24a87-133">[!INCLUDE[tsql](../../includes/tsql-md.md)]テストコマンドスクリプトをファイルにコピーし、として `test.sql` サンプルディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="24a87-133">Copy [!INCLUDE[tsql](../../includes/tsql-md.md)] test command script into a file and save it as `test.sql` in the sample directory.</span></span>  
  
8.  <span data-ttu-id="24a87-134">次のコマンドを使用してテスト スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="24a87-134">Execute the test script with the following command</span></span>  
  
    -   `sqlcmd -E -I -i test.sql`  
  
9. <span data-ttu-id="24a87-135">[!INCLUDE[tsql](../../includes/tsql-md.md)] クリーンアップ スクリプトをファイルにコピーし、`cleanup.sql` としてサンプル ディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="24a87-135">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] cleanup script into a file and save it as `cleanup.sql` in the sample directory.</span></span>  
  
10. <span data-ttu-id="24a87-136">次のコマンドを使用してこのスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="24a87-136">Execute the script with the  following command</span></span>  
  
    -   `sqlcmd -E -I -i cleanup.sql`  
  
  
## <a name="sample-code"></a><span data-ttu-id="24a87-137">サンプル コード</span><span class="sxs-lookup"><span data-stu-id="24a87-137">Sample Code</span></span>  
 <span data-ttu-id="24a87-138">このサンプルのコード リストを次に示します。</span><span class="sxs-lookup"><span data-stu-id="24a87-138">The following are the code listings for this sample.</span></span>  
  
 <span data-ttu-id="24a87-139">C#</span><span class="sxs-lookup"><span data-stu-id="24a87-139">C#</span></span>  
  
```  
  
using System;  
using System.IO;  
using System.Collections;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlTypes;  
using System.Data.Sql;  
using System.Text.RegularExpressions;  
using Microsoft.SqlServer.Server;  
  
    /// <summary>  
    /// This class is provides regular expression operations for Transact-SQL callers  
    /// </summary>  
    public sealed class RegularExpression  
    {  
        private RegularExpression()  
        {  
  
        }  
  
        /// <summary>  
        /// This method returns a table of matches, groups, and captures based on the input  
        /// string and pattern string provided.  
        /// </summary>  
        /// <param name="sqlInput">What to match against</param>  
        /// <param name="sqlPattern">What to look for</param>  
        /// <returns>An object which appears to be reading from SQL Server but which in fact is reading  
        ///          from a memory based representation of the data.</returns>  
        [SqlFunction(FillRowMethodName = "FillRow")]  
        public static IEnumerable Matches(SqlString sqlInput, SqlString sqlPattern)  
        {  
            string input = (sqlInput.IsNull) ? string.Empty : sqlInput.Value;  
            string pattern = (sqlPattern.IsNull) ? string.Empty : sqlPattern.Value;  
  
            return GetMatches(input, pattern);  
        }  
  
        public static void FillRow(object obj, out int matchId, out int matchIndex, out string matchValue,  
            out int groupId, out int groupIndex, out string groupValue, out int captureIndex,  
            out string captureValue)  
        {  
            MatchResult result = (MatchResult)obj;  
            matchId = result.MatchID;  
            matchIndex = result.MatchIndex;  
            matchValue = result.MatchValue;  
            groupId = result.GroupID;  
            groupIndex = result.GroupIndex;  
            groupValue = result.GroupValue;  
            captureIndex = result.CaptureIndex;  
            captureValue = result.CaptureValue;  
        }  
  
        /// <summary>  
        ///     Generates a list of Match/Group/Capture tuples represented using the  
        ///     MatchResult struct based on the regular expression match of the input  
        ///     string and pattern string provided.  
        /// </summary>  
        /// <param name="input">What to match</param>  
        /// <param name="pattern">What to look for</param>  
        /// <returns>A list of Match/Group/Capture tuples</returns>  
        private static List<MatchResult> GetMatches(string input, string pattern)  
        {  
            List<MatchResult> result = new List<MatchResult>();  
            int matchId = 0;  
            int groupId = 0;  
            foreach (Match m in Regex.Matches(input, pattern))  
            {  
                if (m.Groups.Count < 1)  
                    result.Add(new MatchResult(matchId, m.Index, m.Value, -1, -1, string.Empty, -1, string.Empty));  
                else  
                {  
                    groupId = 0;  
                    foreach (Group g in m.Groups)  
                    {  
                        if (g.Captures.Count < 1)  
                            result.Add(new MatchResult(matchId, m.Index, m.Value,  
                                groupId, g.Index, g.Value, -1, string.Empty));  
                        else  
                        {  
                            foreach (Capture c in m.Groups)  
                            {  
                                result.Add(new MatchResult(matchId, m.Index, m.Value,  
                                    groupId, g.Index, g.Value, c.Index, c.Value));  
                            }  
                        }  
  
                        groupId += 1;  
                    }  
                }  
  
                matchId += 1;  
            }  
  
            return result;  
        }  
  
        /// <summary>  
        ///     This method performs a pattern based substitution based on the provided input string, pattern  
        ///     string, and replacement string.  
        /// </summary>  
        /// <param name="sqlInput">The source material</param>  
        /// <param name="sqlPattern">How to parse the source material</param>  
        /// <param name="sqlReplacement">What the output should look like</param>  
        /// <returns></returns>  
        public static string Replace(SqlString sqlInput, SqlString sqlPattern, SqlString sqlReplacement)  
        {  
            string input = (sqlInput.IsNull) ? string.Empty : sqlInput.Value;  
            string pattern = (sqlPattern.IsNull) ? string.Empty : sqlPattern.Value;  
            string replacement = (sqlReplacement.IsNull) ? string.Empty : sqlReplacement.Value;  
            return Regex.Replace(input, pattern, replacement);  
        }  
    }  
  
    /// <summary>  
    /// This struct is used trepresents a Match/Group/Capture tuple.  Instances of this struct are  
    /// created by the GetMatches method.  
    /// </summary>  
    internal struct MatchResult  
    {  
        /// <summary>  
        /// Which match this is  
        /// </summary>  
        private int _matchID;  
        public int MatchID  
        {  
            get  
            {  
                return this._matchID;  
            }  
        }  
  
        /// <summary>  
        /// Where the match starts in the input string  
        /// </summary>  
        private int _matchIndex;  
        public int MatchIndex  
        {  
            get  
            {  
                return this._matchIndex;  
            }  
        }  
  
        /// <summary>  
        /// What string matched the pattern  
        /// </summary>  
        private string _matchValue;  
        public string MatchValue  
        {  
            get  
            {  
                return this._matchValue;  
            }  
        }  
  
        /// <summary>  
        /// Which matching group this is  
        /// </summary>  
        private int _groupID;  
        public int GroupID  
        {  
            get  
            {  
                return this._groupID;  
            }  
        }  
  
        /// <summary>  
        /// Where this group starts in the input string  
        /// </summary>  
        private int _groupIndex;  
        public int GroupIndex  
        {  
            get  
            {  
                return this._groupIndex;  
            }  
        }  
  
        /// <summary>  
        /// What the group matched in the input string  
        /// </summary>  
        private string _groupValue;  
        public string GroupValue  
        {  
            get  
            {  
                return this._groupValue;  
            }  
        }  
  
        /// <summary>  
        /// Where this capture starts in the input string  
        /// </summary>  
        private int _captureIndex;  
        public int CaptureIndex  
        {  
            get  
            {  
                return this._captureIndex;  
            }  
        }  
  
        /// <summary>  
        /// What the capture matched in the input string  
        /// </summary>  
        private string _captureValue;  
        public string CaptureValue  
        {  
            get  
            {  
                return this._captureValue;  
            }  
        }  
  
        /// <summary>  
        ///     A convenient constructor which fills in all the fields contained in this struct.  
        /// </summary>  
        /// <param name="matchID">Which match this is</param>  
        /// <param name="matchIndex">Where the match starts in the input string</param>  
        /// <param name="matchValue">What string matched the pattern</param>  
        /// <param name="groupID">Which matching group this is</param>  
        /// <param name="groupIndex">Where this group starts in the input string</param>  
        /// <param name="groupValue">What the group matched in the input string</param>  
        /// <param name="captureIndex">Where this capture starts in the input string</param>  
        /// <param name="captureValue">What the capture matched in the input string</param>  
        public MatchResult(int matchId, int matchIndex, string matchValue,  
            int groupId, int groupIndex, string groupValue,  
            int captureIndex, string captureValue)  
        {  
            this._matchID = matchId;  
            this._matchIndex = matchIndex;  
            this._matchValue = matchValue;  
            this._groupID = groupId;  
            this._groupIndex = groupIndex;  
            this._groupValue = groupValue;  
            this._captureIndex = captureIndex;  
            this._captureValue = captureValue;  
        }  
    }  
  
    public sealed class StringSplitter  
    {  
  
        /// <summary>  
        /// The streaming table-valued function used to split the string into a relation  
        /// </summary>  
        /// <param name="argument"></param>  
        /// <returns></returns>  
        [SqlFunction(FillRowMethodName = "FillRow")]  
        public static IEnumerable Split(SqlString argument)  
        {  
            string value;  
            if (argument.IsNull)  
                value = "";  
            else  
                value = argument.Value;  
            return value.Split(',');  
        }  
  
        public static void FillRow(Object obj, out string stringElement)  
        {  
            stringElement = (string)obj;  
        }  
  
        /// <summary>  
        /// Don't allow callers to create instances of this class  
        /// </summary>  
        private StringSplitter() { }  
    }  
    [Serializable]  
    [Microsoft.SqlServer.Server.SqlUserDefinedAggregate(  
        Microsoft.SqlServer.Server.Format.UserDefined, //use clr serialization to serialize the intermediate result  
        IsInvariantToNulls = true,//optimizer property  
        IsInvariantToDuplicates = false,//optimizer property  
        IsInvariantToOrder = false,//optimizer property  
        MaxByteSize = 8000)//maximum size in bytes of persisted value  
        ]  
    public class Concatenate : Microsoft.SqlServer.Server.IBinarySerialize  
    {  
        /// <summary>  
        /// The variable that holds the intermediate result of the concatenation  
        /// </summary>  
        private StringBuilder intermediateResult;  
  
        /// <summary>  
        /// Initialize the internal data structures  
        /// </summary>  
        public void Init()  
        {  
            intermediateResult = new StringBuilder();  
        }  
  
        /// <summary>  
        /// Accumulate the next value, nop if the value is null  
        /// </summary>  
        /// <param name="value"></param>  
        public void Accumulate(SqlString value)  
        {  
  
            if (value.IsNull)  
            {  
                return;  
            }  
            intermediateResult.Append(value.Value).Append(',');  
  
        }  
  
        /// <summary>  
        /// Merge the partially computed aggregate with this aggregate.  
        /// </summary>  
        /// <param name="other"></param>  
        public void Merge(Concatenate other)  
        {  
            intermediateResult.Append(other.intermediateResult);  
        }  
  
        /// <summary>  
        /// Called at the end of aggregation, to return the results of the aggregation  
        /// </summary>  
        /// <returns></returns>  
        public SqlString Terminate()  
        {  
            string output = string.Empty;  
            //delete the trailing comma, if any  
            if (intermediateResult != null && intermediateResult.Length > 0)  
                output = intermediateResult.ToString(0, intermediateResult.Length - 1);  
            return new SqlString(output);  
        }  
  
        public void Read(BinaryReader r)  
        {  
            if (r == null) throw new ArgumentNullException("r");  
            intermediateResult = new StringBuilder(r.ReadString());  
        }  
  
        public void Write(BinaryWriter w)  
        {  
            if (w == null) throw new ArgumentNullException("w");  
            w.Write(intermediateResult.ToString());  
        }  
    }  
  
```  
  
 <span data-ttu-id="24a87-140">VB.NET</span><span class="sxs-lookup"><span data-stu-id="24a87-140">VB.NET</span></span>  
  
```  
Imports Microsoft.VisualBasic  
Imports Microsoft.SqlServer.Server  
Imports System  
Imports System.Collections  
Imports System.Collections.Generic  
Imports System.Data  
Imports System.Data.SqlTypes  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Linq  
Imports System.Runtime.InteropServices  
Imports System.Text  
Imports System.Text.RegularExpressions  
  
<Serializable(), Microsoft.SqlServer.Server.SqlUserDefinedAggregate(Microsoft.SqlServer.Server.Format.UserDefined, IsInvariantToNulls:=True, IsInvariantToDuplicates:=False, IsInvariantToOrder:=False, MaxByteSize:=8000)> _  
Public Class Concatenate  
    'use clr serialization to serialize the intermediate result  
    'optimizer property  
    'optimizer property  
    'optimizer property  
    'maximum size in bytes of persisted value  
    Implements Microsoft.SqlServer.Server.IBinarySerialize  
  
    ''' <summary>  
    ''' The variable that holds the intermediate result of the concatenation  
    ''' </summary>  
    Private intermediateResult As StringBuilder  
  
    ''' <summary>  
    ''' Initialize the internal data structures  
    ''' </summary>  
    Public Sub Init()  
        intermediateResult = New StringBuilder()  
    End Sub  
  
    ''' <summary>  
    ''' Accumulate the next value, nop if the value is null  
    ''' </summary>  
    ''' <param name="value"></param>  
    Public Sub Accumulate(ByVal value As SqlString)  
        If value.IsNull Then  
            Return  
        End If  
  
        intermediateResult.Append(value.Value).Append(","c)  
    End Sub  
  
    ''' <summary>  
    ''' Merge the partially computed aggregate with this aggregate.  
    ''' </summary>  
    ''' <param name="other"></param>  
    Public Sub Merge(ByVal other As Concatenate)  
        intermediateResult.Append(other.intermediateResult)  
    End Sub  
  
    ''' <summary>  
    ''' Called at the end of aggregation, to return the results of the aggregation  
    ''' </summary>  
    ''' <returns></returns>  
    Public Function Terminate() As SqlString  
        Dim output As String = String.Empty  
  
        'delete the trailing comma, if any  
        If Not (intermediateResult Is Nothing) AndAlso intermediateResult.Length > 0 Then  
            output = intermediateResult.ToString(0, intermediateResult.Length - 1)  
        End If  
  
        Return New SqlString(output)  
    End Function  
  
    Public Sub Read(ByVal r As BinaryReader) Implements Microsoft.SqlServer.Server.IBinarySerialize.Read  
        If r Is Nothing Then  
            Throw New ArgumentNullException("r")  
        End If  
        intermediateResult = New StringBuilder(r.ReadString())  
    End Sub  
  
    Public Sub Write(ByVal w As BinaryWriter) Implements Microsoft.SqlServer.Server.IBinarySerialize.Write  
        If w Is Nothing Then  
            Throw New ArgumentNullException("w")  
        End If  
        w.Write(intermediateResult.ToString())  
    End Sub  
End Class  
  
Public NotInheritable Class RegularExpression  
  
    Private Sub New()  
    End Sub  
  
    ''' <summary>  
    ''' This method returns a table of matches, groups, and captures based on the input  
    ''' string and pattern string provided.  
    ''' </summary>  
    ''' <param name="sqlInput">What to match against</param>  
    ''' <param name="sqlPattern">What to look for</param>  
    ''' <returns>An object which appears to be reading from SQL Server but which in fact is reading  
    '''          from a memory based representation of the data.</returns>  
    <SqlFunction(Name:="RegexMatches", FillRowMethodName:="FillMatchRow", _  
        TableDefinition:="MatchID int, MatchIndex int, MatchValue nvarchar(4000), GroupID int, GroupIndex int, GroupValue nvarchar(4000), CaptureIndex int, CaptureValue nvarchar(4000)")> _  
    Public Shared Function Matches(ByVal sqlInput As SqlString, ByVal sqlPattern As SqlString) As IEnumerable  
        Dim input As String = String.Empty  
        If Not sqlInput.IsNull Then  
            input = sqlInput.Value  
        End If  
  
        Dim pattern As String = String.Empty  
        If Not sqlPattern.IsNull Then  
            pattern = sqlPattern.Value  
        End If  
  
        Return GetMatches(input, pattern)  
    End Function  
  
    ''' <summary>  
    ''' Invoked by SQL Server when returning a row of the TVF.  Splits the MatchResult object into  
    ''' the separate pieces of data which will form the columns of the row.  
    ''' </summary>  
    ''' <param name="row"></param>  
    ''' <param name="matchID"></param>  
    ''' <param name="matchIndex"></param>  
    ''' <param name="matchValue"></param>  
    ''' <param name="groupID"></param>  
    ''' <param name="groupIndex"></param>  
    ''' <param name="groupValue"></param>  
    ''' <param name="captureIndex"></param>  
    ''' <param name="captureValue"></param>  
  
    Private Shared Sub FillMatchRow(ByVal row As Object, <Out()> ByRef matchId As Integer, _  
        <Out()> ByRef matchIndex As Integer, <Out()> ByRef matchValue As String, <Out()> ByRef groupId As Integer, _  
        <Out()> ByRef groupIndex As Integer, <Out()> ByRef groupValue As String, <Out()> ByRef captureIndex As Integer, _  
        <Out()> ByRef captureValue As String)  
  
        Dim result As MatchResult  
  
        result = CType(row, MatchResult)  
  
        matchId = result.MatchID  
        matchIndex = result.MatchIndex  
        matchValue = result.MatchValue  
        groupId = result.GroupID  
        groupIndex = result.GroupIndex  
        groupValue = result.GroupValue  
        captureIndex = result.CaptureIndex  
        captureValue = result.CaptureValue  
    End Sub  
  
    ''' <summary>  
    '''     Generates a list of Match/Group/Capture tuples represented using the  
    '''     MatchResult struct based on the regular expression match of the input  
    '''     string and pattern string provided.  
    ''' </summary>  
    ''' <param name="input">What to match</param>  
    ''' <param name="pattern">What to look for</param>  
    ''' <returns>A list of Match/Group/Capture tuples</returns>  
    Private Shared Function GetMatches(ByVal input As String, ByVal pattern As String) As List(Of MatchResult)  
        Dim result As List(Of MatchResult) = New List(Of MatchResult)()  
        Dim matchID As Integer = 0  
        Dim groupID As Integer = 0  
  
        For Each m As Match In Regex.Matches(input, pattern)  
            If m.Groups.Count < 1 Then  
                result.Add(New MatchResult(matchID, m.Index, m.Value, -1, -1, _  
                    String.Empty, -1, String.Empty))  
            Else  
                groupID = 0  
                For Each g As Group In m.Groups  
                    If g.Captures.Count < 1 Then  
                        result.Add(New MatchResult(matchID, m.Index, m.Value, _  
                            groupID, g.Index, g.Value, -1, String.Empty))  
                    Else  
                        For Each c As Capture In m.Groups  
                            result.Add(New MatchResult(matchID, m.Index, _  
                                m.Value, groupID, g.Index, g.Value, c.Index, _  
                                c.Value))  
                        Next  
                    End If  
  
                    groupID += 1  
                Next  
            End If  
  
            matchID += 1  
        Next  
  
        Return result  
    End Function  
  
    ''' <summary>  
    '''     This method performs a pattern based substitution based on the provided input string, pattern  
    '''     string, and replacement string.  
    ''' </summary>  
    ''' <param name="sqlInput">The source material</param>  
    ''' <param name="sqlPattern">How to parse the source material</param>  
    ''' <param name="sqlReplacement">What the output should look like</param>  
    ''' <returns></returns>  
    <SqlFunction(Name:="RegexReplace", DataAccess:=DataAccessKind.None)> _  
    Public Shared Function Replace(ByVal sqlInput As SqlString, ByVal sqlPattern As SqlString, ByVal sqlReplacement As SqlString) As String  
        Dim input As String = String.Empty  
  
        If Not sqlInput.IsNull Then  
            input = sqlInput.Value  
        End If  
  
        Dim pattern As String = String.Empty  
  
        If Not sqlPattern.IsNull Then  
            pattern = sqlPattern.Value.ToString()  
        End If  
  
        Dim replacement As String = String.Empty  
  
        If Not sqlReplacement.IsNull Then  
            replacement = sqlReplacement.Value.ToString()  
        End If  
  
        Return Regex.Replace(input, pattern, replacement)  
    End Function  
End Class  
  
''' <summary>  
''' This struct is used to represent a Match/Group/Capture tuple.  Instances of   
''' this struct are created by the GetMatches method.  
''' </summary>  
Friend Structure MatchResult  
    ''' <summary>  
    ''' Which match this is  
    ''' </summary>  
    Private _matchID As Integer  
  
    Friend ReadOnly Property MatchID() As Integer  
        Get  
            Return Me._matchID  
        End Get  
    End Property  
  
    ''' <summary>  
    ''' Where the match starts in the input string  
    ''' </summary>  
    Private _matchIndex As Integer  
  
    Friend ReadOnly Property MatchIndex() As Integer  
        Get  
            Return Me._matchIndex  
        End Get  
    End Property  
  
    ''' <summary>  
    ''' What string matched the pattern  
    ''' </summary>  
    Private _matchValue As String  
  
    Friend ReadOnly Property MatchValue() As String  
        Get  
            Return Me._matchValue  
        End Get  
    End Property  
  
    ''' <summary>  
    ''' Which matching group this is  
    ''' </summary>  
    Private _groupID As Integer  
  
    Friend ReadOnly Property GroupID() As Integer  
        Get  
            Return Me._groupID  
        End Get  
    End Property  
  
    ''' <summary>  
    ''' Where this group starts in the input string  
    ''' </summary>  
    Private _groupIndex As Integer  
  
    Friend ReadOnly Property GroupIndex() As Integer  
        Get  
            Return Me._groupIndex  
        End Get  
    End Property  
  
    ''' <summary>  
    ''' What the group matched in the input string  
    ''' </summary>  
    Private _groupValue As String  
  
    Friend ReadOnly Property GroupValue() As String  
        Get  
            Return Me._groupValue  
        End Get  
    End Property  
  
    ''' <summary>  
    ''' Where this capture starts in the input string  
    ''' </summary>  
    Private _captureIndex As Integer  
  
    Friend ReadOnly Property CaptureIndex() As Integer  
        Get  
            Return Me._captureIndex  
        End Get  
    End Property  
  
    ''' <summary>  
    ''' What the capture matched in the input string  
    ''' </summary>  
    Private _captureValue As String  
  
    Friend ReadOnly Property CaptureValue() As String  
        Get  
            Return Me._captureValue  
        End Get  
    End Property  
  
    ''' <summary>  
    '''     A convenient constructor which fills in all the fields contained in this struct.  
    ''' </summary>  
    ''' <param name="matchID">Which match this is</param>  
    ''' <param name="matchIndex">Where the match starts in the input string</param>  
    ''' <param name="matchValue">What string matched the pattern</param>  
    ''' <param name="groupID">Which matching group this is</param>  
    ''' <param name="groupIndex">Where this group starts in the input string</param>  
    ''' <param name="groupValue">What the group matched in the input string</param>  
    ''' <param name="captureIndex">Where this capture starts in the input string</param>  
    ''' <param name="captureValue">What the capture matched in the input string</param>  
    Friend Sub New(ByVal matchID As Integer, ByVal matchIndex As Integer, ByVal matchValue As String, ByVal groupID As Integer, ByVal groupIndex As Integer, ByVal groupValue As String, ByVal captureIndex As Integer, ByVal captureValue As String)  
        Me._matchID = matchID  
        Me._matchIndex = matchIndex  
        Me._matchValue = matchValue  
        Me._groupID = groupID  
        Me._groupIndex = groupIndex  
        Me._groupValue = groupValue  
        Me._captureIndex = captureIndex  
        Me._captureValue = captureValue  
    End Sub  
End Structure  
Public NotInheritable Class StringSplitter  
  
    ''' <summary>  
    ''' The streaming table-valued function used to split the string into a relation  
    ''' </summary>  
    ''' <param name="argument"></param>  
    ''' <returns></returns>  
    <SqlFunction(Name:="Split", DataAccess:=DataAccessKind.None, FillRowMethodName:="FillSplitRow", _  
        TableDefinition:="StringElement nvarchar(128) COLLATE Latin1_General_CI_AS")> _  
    Public Shared Function Split(ByVal argument As SqlString) As IEnumerable  
        Dim value As String  
  
        If argument.IsNull Then  
            value = String.Empty  
        Else  
            value = argument.Value  
        End If  
  
        Return value.Split(","c)  
    End Function  
  
    Private Shared Sub FillSplitRow(ByVal row As Object, ByRef stringElement As String)  
        stringElement = CType(row, String)  
    End Sub  
  
    ''' <summary>  
    ''' Don't allow callers to create instances of this class  
    ''' </summary>  
    Private Sub New()  
    End Sub  
End Class  
  
```  
  
 <span data-ttu-id="24a87-141">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] インストール スクリプト (`Install.sql`) は、アセンブリを展開し、データベースにストアド プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="24a87-141">This is the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation script (`Install.sql`), which deploys the assembly and creates the stored procedure in the database.</span></span>  
  
```  
USE AdventureWorks  
GO  
  
IF OBJECT_ID(N'RegexMatches', N'FT') is not null  
DROP Function RegexMatches;  
GO  
  
IF OBJECT_ID(N'Split', N'FT') is not null  
DROP Function Split;  
GO  
  
IF OBJECT_ID(N'RegexReplace', N'FS') is not null  
DROP Function RegexReplace;  
GO  
  
IF OBJECT_ID(N'Concatenate', N'AF') is not null  
DROP Aggregate Concatenate;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'StringUtils')  
DROP ASSEMBLY StringUtils;  
GO  
  
DECLARE @SamplePath nvarchar(1024)  
-- You will need to modify the value of the this variable if you have installed the sample someplace other than the default location.  
Set @SamplePath = 'C:\MySample\'  
CREATE ASSEMBLY [StringUtils]   
FROM @SamplePath + 'StringUtils.dll'  
WITH permission_set = Safe;  
GO  
  
CREATE AGGREGATE [dbo].[Concatenate](@input nvarchar(4000))  
RETURNS nvarchar(4000)  
EXTERNAL NAME [StringUtils].[Concatenate];  
GO  
  
CREATE FUNCTION [dbo].[Split](@input nvarchar(4000))   
RETURNS  TABLE(StringElement nvarchar(128) COLLATE Latin1_General_CI_AS)  
AS EXTERNAL NAME [StringUtils].[StringSplitter].[Split];  
GO  
  
CREATE FUNCTION [RegexMatches] (@input nvarchar(max), @pattern nvarchar(max))  
RETURNS TABLE(  
MatchID int,  
    MatchIndex int,  
    MatchValue nvarchar(4000),  
GroupID int,  
GroupIndex int,  
GroupValue nvarchar(4000),  
CaptureIndex int,  
CaptureValue nvarchar(4000))  
AS EXTERNAL NAME [StringUtils].[RegularExpression].[Matches];  
GO  
  
CREATE FUNCTION [RegexReplace] (@input nvarchar(max), @pattern nvarchar(max), @replacement nvarchar(max))  
RETURNS nvarchar(max)  
AS EXTERNAL NAME [StringUtils].[RegularExpression].[Replace]  
GO  
```  
  
 <span data-ttu-id="24a87-142">次の `test.sql` は、関数を実行してサンプルをテストします。</span><span class="sxs-lookup"><span data-stu-id="24a87-142">This is `test.sql`, which tests the sample by executing the functions.</span></span>  
  
```sql  
USE AdventureWorks  
GO  
  
-- Invoke the tvf  
SELECT * FROM dbo.Split('will,this,work');  
GO  
  
-- Invoke the aggregate over the results of the tvf  
SELECT dbo.Concatenate(StringElement) FROM dbo.Split('will,this,also,work');  
GO  
  
-- Find two word pairs where the first word contains an 'r'  
SELECT MatchID, MatchIndex, MatchValue,   
  GroupID, GroupIndex, GroupValue,   
  CaptureIndex, CaptureValue  
FROM dbo.RegexMatches('The quick red fox jumped over the lazy brown dog', '(\w*r\w*)\s(\w+)');  
GO  
  
-- A variant of the above with no backtracking  
SELECT MatchID, MatchIndex, MatchValue,   
  GroupID, GroupIndex, GroupValue,   
  CaptureIndex, CaptureValue  
FROM dbo.RegexMatches('The quick red fox jumped over the lazy brown dog', '(?>\w*r\w*)\s(?>\w+)');  
GO  
  
-- Swap the subject of the sentence with the object of the sentence.  
SELECT dbo.RegexReplace('The quick red fox jumped over the lazy brown dog',   
'^The (?<fox>(?:[\w]+\s){3})jumped over the (?<dog>(?:[\w]+\s){2}(?:[\w]+))$',  
  
'The ${dog} jumped over the ${fox}');  
```  
  
 <span data-ttu-id="24a87-143">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] は、アセンブリと関数をデータベースから削除します。</span><span class="sxs-lookup"><span data-stu-id="24a87-143">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] removes the assembly and functions from the database.</span></span>  
  
```  
USE AdventureWorks  
GO  
  
IF OBJECT_ID(N'RegexMatches', N'FT') is not null  
DROP Function RegexMatches;  
GO  
  
IF OBJECT_ID(N'Split', N'FT') is not null  
DROP Function Split;  
GO  
  
IF OBJECT_ID(N'RegexReplace', N'FS') is not null  
DROP Function RegexReplace;  
GO  
  
IF OBJECT_ID(N'Concatenate', N'AF') is not null  
DROP Aggregate Concatenate;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'StringUtils')  
DROP ASSEMBLY StringUtils;  
  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="24a87-144">参照</span><span class="sxs-lookup"><span data-stu-id="24a87-144">See Also</span></span>  
 [<span data-ttu-id="24a87-145">CLR &#40;共通言語ランタイム&#41; 統合の使用シナリオと例</span><span class="sxs-lookup"><span data-stu-id="24a87-145">Usage Scenarios and Examples for Common Language Runtime &#40;CLR&#41; Integration</span></span>](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  

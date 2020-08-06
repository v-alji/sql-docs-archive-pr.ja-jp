---
title: 補助対応の文字列操作のサンプル |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: 343a1cd6-94e9-4200-9d17-11cef0d73f73
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d3364e43df19319fe1cdcad5ce7f7a8fd2bbbf6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716702"
---
# <a name="supplementary-aware-string-manipulation-sample"></a><span data-ttu-id="b8729-102">補助文字対応文字列操作サンプル</span><span class="sxs-lookup"><span data-stu-id="b8729-102">Supplementary-Aware String Manipulation Sample</span></span>
  <span data-ttu-id="b8729-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用のこのサンプルは、補助文字に対応した文字列処理を示します。</span><span class="sxs-lookup"><span data-stu-id="b8729-103">This sample for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] demonstrates supplementary character aware string processing.</span></span> <span data-ttu-id="b8729-104">このサンプルでは、組み込み関数と同じ文字列操作機能を提供する、Transact-SQL の 5 つの文字列関数の実装を示します。ただしこのサンプルの文字列操作関数では、Unicode 文字列および補助文字文字列の両方を処理することができます。</span><span class="sxs-lookup"><span data-stu-id="b8729-104">This sample shows the implementation of five Transact-SQL string functions that provide the same string manipulation functions as the built-in functions, but with additional supplementary character-aware capability to handle both Unicode and supplementary character strings.</span></span> <span data-ttu-id="b8729-105">5つの関数は、レンズ () であり、 `lefts(), rights(), subs()` `replace_s()` 組み込み関数 `LEN(), LEFT(), RIGHT(), SUBSTRING()` と文字列関数に相当し `REPLACE()` ます。</span><span class="sxs-lookup"><span data-stu-id="b8729-105">The five functions are lens(), `lefts(), rights(), subs()` and `replace_s()` which are equivalent to the built-in functions `LEN(), LEFT(), RIGHT(), SUBSTRING()` and `REPLACE()` string functions.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b8729-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="b8729-106">Prerequisites</span></span>  
 <span data-ttu-id="b8729-107">このプロジェクトを作成して実行するには、次のソフトウェアがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8729-107">To create and run this project the following the following software must be installed:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b8729-108">または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express。</span><span class="sxs-lookup"><span data-stu-id="b8729-108">or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express.</span></span> <span data-ttu-id="b8729-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express ドキュメントとサンプルの [Web サイト](https://www.microsoft.com/sql-server/sql-server-editions-express)から無償で入手できます。</span><span class="sxs-lookup"><span data-stu-id="b8729-109">You can obtain [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express free of charge from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express Documentation and Samples [Web site](https://www.microsoft.com/sql-server/sql-server-editions-express)</span></span>  
  
-   <span data-ttu-id="b8729-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] デベロッパー [Web サイト](https://go.microsoft.com/fwlink/?linkid=62796)から入手できる AdventureWorks データベース。</span><span class="sxs-lookup"><span data-stu-id="b8729-110">The AdventureWorks database that is available at the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Developer [Web site](https://go.microsoft.com/fwlink/?linkid=62796)</span></span>  
  
-   <span data-ttu-id="b8729-111">.NET Framework SDK 2.0 以降または Microsoft Visual Studio 2005 以降。</span><span class="sxs-lookup"><span data-stu-id="b8729-111">.NET Framework SDK 2.0 or later or Microsoft Visual Studio 2005 or later.</span></span> <span data-ttu-id="b8729-112">.NET Framework SDK は無償で入手できます。</span><span class="sxs-lookup"><span data-stu-id="b8729-112">You can obtain .NET Framework SDK free of charge.</span></span>  
  
-   <span data-ttu-id="b8729-113">また、次の条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8729-113">In addition, the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="b8729-114">使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスで CLR 統合が有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8729-114">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using must have CLR integration enabled.</span></span>  
  
-   <span data-ttu-id="b8729-115">CLR 統合を有効にするには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="b8729-115">In order to enable CLR integration, perform the following steps:</span></span>  
  
    #### <a name="enabling-clr-integration"></a><span data-ttu-id="b8729-116">CLR 統合の有効化</span><span class="sxs-lookup"><span data-stu-id="b8729-116">Enabling CLR Integration</span></span>  
  
    -   <span data-ttu-id="b8729-117">以下の [!INCLUDE[tsql](../../includes/tsql-md.md)] コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="b8729-117">Execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] commands:</span></span>  
  
     `sp_configure 'clr enabled', 1`  
  
     `GO`  
  
     `RECONFIGURE`  
  
     `GO`  
  
    > [!NOTE]  
    >  <span data-ttu-id="b8729-118">CLR を有効にするには、 `ALTER SETTINGS` サーバーレベルの権限が必要です。この権限は、 `sysadmin` 固定サーバーロールおよびのメンバーによって暗黙的に保持されてい `serveradmin` ます。</span><span class="sxs-lookup"><span data-stu-id="b8729-118">To enable CLR, you must have `ALTER SETTINGS` server level permission, which is implicitly held by members of the `sysadmin` and `serveradmin` fixed server roles.</span></span>  
  
-   <span data-ttu-id="b8729-119">使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに AdventureWorks データベースがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8729-119">The AdventureWorks database must be installed on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using.</span></span>  
  
-   <span data-ttu-id="b8729-120">使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの管理者でない場合は、インストールを完了するために **CreateAssembly** 権限が管理者から付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8729-120">If you are not an administrator for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using, you must have an administrator grant you **CreateAssembly**  permission to complete the installation.</span></span>  
  
## <a name="building-the-sample"></a><span data-ttu-id="b8729-121">サンプルのビルド</span><span class="sxs-lookup"><span data-stu-id="b8729-121">Building the Sample</span></span>  
  
#### <a name="create-and-run-the-sample-by-using-the-following-instructions"></a><span data-ttu-id="b8729-122">次の手順に従ってサンプルを作成し、実行します。</span><span class="sxs-lookup"><span data-stu-id="b8729-122">Create and run the sample by using the following instructions:</span></span>  
  
1.  <span data-ttu-id="b8729-123">Visual Studio または .NET Framework のコマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="b8729-123">Open a Visual Studio or .NET Framework command prompt.</span></span>  
  
2.  <span data-ttu-id="b8729-124">必要な場合は、サンプル用のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="b8729-124">If necessary, create a directory for your sample.</span></span> <span data-ttu-id="b8729-125">この例では C:\MySample を使用します。</span><span class="sxs-lookup"><span data-stu-id="b8729-125">For this example, we will use C:\MySample.</span></span>  
  
3.  <span data-ttu-id="b8729-126">この例では署名付きアセンブリが必要であるため、次のコマンドを入力して非対称キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b8729-126">Since this example requires a signed assembly, create an asymmetric key by typing the command:</span></span>  
  
     `sn -k SampleKey.snk`  
  
4.  <span data-ttu-id="b8729-127">選択した言語に応じて次のいずれかをコマンド プロンプトで実行し、サンプル コードをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="b8729-127">Compile the sample code from the command line prompt by executing one of the following, depending on your choice of language.</span></span>  
  
    -   `Vbc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Xml.dll  /keyfile:Key.snk  /target:library SurrogateStringFunction.vb`  
  
    -   `Csc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.XML.dll  /keyfile:Key.snk /target:library SurrogateStringFunction.cs`  
  
5.  <span data-ttu-id="b8729-128">[!INCLUDE[tsql](../../includes/tsql-md.md)] インストール コードをファイルにコピーし、`Install.sql` としてサンプル ディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="b8729-128">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation code into a file and save it as `Install.sql` in the sample directory.</span></span>  
  
6.  <span data-ttu-id="b8729-129">次のコマンドを実行して、アセンブリとストアド プロシージャを配置します。</span><span class="sxs-lookup"><span data-stu-id="b8729-129">Deploy the assembly and stored procedure by executing</span></span>  
  
    -   `sqlcmd -E -I -i install.sql -v root = "C:\MySample\"`  
  
7.  <span data-ttu-id="b8729-130">[!INCLUDE[tsql](../../includes/tsql-md.md)]テストコマンドスクリプトをファイルにコピーし、として `test.sql` サンプルディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="b8729-130">Copy [!INCLUDE[tsql](../../includes/tsql-md.md)] test command script into a file and save it as `test.sql` in the sample directory.</span></span>  
  
8.  <span data-ttu-id="b8729-131">次のコマンドを使用してテスト スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="b8729-131">Execute the test script with the following command</span></span>  
  
    -   `sqlcmd -E -I -i test.sql`  
  
9. <span data-ttu-id="b8729-132">[!INCLUDE[tsql](../../includes/tsql-md.md)] クリーンアップ スクリプトをファイルにコピーし、`cleanup.sql` としてサンプル ディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="b8729-132">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] cleanup script into a file and save it as `cleanup.sql` in the sample directory.</span></span>  
  
10. <span data-ttu-id="b8729-133">次のコマンドを使用してこのスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="b8729-133">Execute the script with the  following command</span></span>  
  
    -   `sqlcmd -E -I -i cleanup.sql`  
  
## <a name="sample-code"></a><span data-ttu-id="b8729-134">サンプル コード</span><span class="sxs-lookup"><span data-stu-id="b8729-134">Sample Code</span></span>  
 <span data-ttu-id="b8729-135">このサンプルのコード リストを次に示します。</span><span class="sxs-lookup"><span data-stu-id="b8729-135">The following are the code listings for this sample.</span></span>  
  
 <span data-ttu-id="b8729-136">C#</span><span class="sxs-lookup"><span data-stu-id="b8729-136">C#</span></span>  
  
```  
using System;  
using System.Globalization;  
using System.Text;  
  
/// <summary>  
/// Include several string functions for T-SQL to manipulate surrogate characters.  
/// </summary>  
public sealed class SurrogateStringFunction  
{  
/// <summary>  
///  
/// </summary>  
private SurrogateStringFunction()  
{}  
  
/// <summary>  
/// LenS is equal to T-SQL string function LEN() which returns the number  
/// of characters, rather than the number of bytes, of the given string expression.  
/// </summary>  
/// <param name="value">The input string.</param>  
/// <returns>The number of characters in the string.</returns>  
public static long LenS(String value)  
{  
if (value == null) throw new ArgumentNullException("value");  
  
int[] myIndex;  
// Remove trailing spaces for situations when the Transact-SQL variable or table column  
// uses a fixed length datatype such as nchar(50).  
// If the trailing spaces are not excluded, this function will return 50 which is not  
// correct or expected.  
myIndex = StringInfo.ParseCombiningCharacters(value.TrimEnd());  
return (null != myIndex) ? myIndex.Length : 0;  
}  
  
/// <summary>  
/// SubS only support character expression of T-SQL funciton SUBSTRING()  
/// which returns part of a string.  
/// </summary>  
/// <param name="value">The input string.</param>  
/// <param name="start">The position of the first character that will be returned.</param>  
/// <param name="length">The number of characters to return.</param>  
/// <returns>The string found at the starting position for the specified  
/// number characters.</returns>  
  
public static String SubS(String value, int start, int length)  
{  
if (value == null) throw new ArgumentNullException("value");  
if (length < 0)  
                throw new ArgumentException("Invalid length parameter passed to the substring function.");  
  
// In Transact-SQL, the substring method initializes to 1. So, start should be initialized to at least 1.  
// Length also has to be at least 1 or the Transact-SQL result would be an empty string.  
            if ((start + length) <= 1)  
                return (String.Empty);  
  
// The 2 if statements below guarantee that the result will match the substring function in   
// Transact-SQL which will initialize start to 1 by subtracting from the length.  
            if (start <= 0 && length > 0)  
                length--;  
  
            if ((start <= 0))  
            {  
                length = length + start;  
                start = 1;  
            }  
  
            int[] myIndex;  
myIndex = StringInfo.ParseCombiningCharacters(value);  
int NumOfIndexes = (null != myIndex) ? myIndex.Length : 0;  
  
            start--;  
            if ((0 <= start) && (start < NumOfIndexes))  
{  
int lastIndex = start + length;  
  
// if we are past the last char, then we get the string  
// up to the last char   
if (lastIndex > (NumOfIndexes - 1))  
{  
return value.Substring(myIndex[start]);  
}  
else  
{  
return value.Substring(myIndex[start], myIndex[lastIndex] - myIndex[start]);  
}  
}  
else  
{  
return String.Empty;  
}  
}  
  
//   
//      
/// <summary>  
/// LeftS is equal to T-SQL string function LEFT() which returns the left  
/// part of a character string with the specified number of characters.  
/// </summary>  
/// <param name="value">The input string.</param>  
/// <param name="start">The position of the first character that will be returned.</param>  
/// <param name="length">The number of characters to return.</param>  
/// <returns>The string found at the starting position for n-length.</returns>  
  
public static String LeftS(String value, int length )  
{  
if (length < 0)  
throw new ArgumentException("length must be a positive integer");  
  
return SubS(value, 1, length);  
}  
  
// RightS is equal to T-SQL string function RIGHT() which returns the right  
//    part of a character string with the specified number of characters.  
  
public static String RightS(String value, int length)  
{  
if (length < 0)  
throw new NotSupportedException("length must be a positive integer");  
if (value == null) throw new ArgumentNullException("value");  
  
int[] myIndex;  
  
myIndex = StringInfo.ParseCombiningCharacters(value);  
int numOfIndexes = (null != myIndex) ? myIndex.Length : 0;  
  
if (numOfIndexes <= length)  
return value;  
  
if (length == 0) return String.Empty;  
  
int virtualStartIndex = numOfIndexes - length;  
int physicalStartIndex = myIndex[virtualStartIndex];  
return value.Substring(physicalStartIndex);  
  
}  
  
//  
// ReplaceS is equal to T-SQL string function REPLACE() which replaces all  
// occurrences of the second given string expression in the first string expression  
// with a third expression.  
//  
public static String ReplaceS(String value, String replaceValue, String newValue)  
{  
StringBuilder result = new StringBuilder(value.Length);  
int[] myIndex;  
int i = 0;  
String upperValue = value.ToUpper(CultureInfo.CurrentUICulture);  
String upperReplaceValue = replaceValue.ToUpper(CultureInfo.CurrentUICulture);  
  
myIndex = StringInfo.ParseCombiningCharacters(upperValue);  
while (i < value.Length)  
{  
int possibleMatch = upperValue.IndexOf(upperReplaceValue, i);  
if (possibleMatch < 0)  
{  
result.Append(value.Substring(i));  
break;  
}  
else  
{  
//Ensure we're not matching a partial surrogate  
int surrogateIndex = Array.IndexOf<int>(myIndex, possibleMatch);  
if (surrogateIndex < 0)  
{  
//We've matched in the middle of a surrogate, skip this match  
//as it is not valid.  
int nextStart = possibleMatch + 1;  
result.Append(value.Substring(i, nextStart-i));  
i = nextStart;  
}  
else  
{  
//This is a valid match.  Make the substitution.  
result.Append(value.Substring(i, possibleMatch - i));  
result.Append(newValue);  
i = possibleMatch + replaceValue.Length;  
}  
}  
}  
return result.ToString();  
}  
}  
```  
  
 <span data-ttu-id="b8729-137">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b8729-137">Visual Basic</span></span>  
  
```  
Imports Microsoft.VisualBasic  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Diagnostics  
Imports System.Globalization  
Imports System.Text  
''' <summary>  
''' Include several string functions for T-SQL to manipulate surrogate characters.  
''' </summary>  
  
Public NotInheritable Class SurrogateStringFunction  
    ''' <summary>  
    ''' Empty default constructor  
    ''' </summary>  
    Private Sub New()  
    End Sub  
  
    ''' <summary>  
    ''' LenS is equal to T-SQL string function LEN() which returns the number  
    ''' of characters, rather than the number of bytes, of the given string expression.  
    ''' </summary>  
    ''' <param name="value">The input string.</param>  
    ''' <returns>The number of characters in the string.</returns>  
    <Microsoft.SqlServer.Server.SqlFunction()> _  
    Public Shared Function LenS(ByVal value As String) As Long  
        If value Is Nothing Then  
            Throw New ArgumentNullException("value")  
        End If  
  
        Dim myIndex() As Integer  
        ' Remove trailing spaces for situations when the Transact-SQL variable or table column  
        ' uses a fixed length datatype such as nchar(50).  
        ' If the trailing spaces are not excluded, this function will return 50 which is not  
        ' correct or expected.  
        myIndex = StringInfo.ParseCombiningCharacters(value.TrimEnd())  
  
        If (myIndex IsNot Nothing) Then  
            Return myIndex.Length  
        Else  
            Return 0  
        End If  
    End Function  
  
    ''' <summary>  
    ''' SubS only support character expression of T-SQL funciton SUBSTRING()  
    ''' which returns part of a string.  
    ''' </summary>  
    ''' <param name="value">The input string.</param>  
    ''' <param name="start">The position of the first character that will be returned.</param>  
    ''' <param name="length">The number of characters to return.</param>  
    ''' <returns>The string found at the starting position for the specified  
    ''' number characters.</returns>  
    <Microsoft.SqlServer.Server.SqlFunction()> _  
    Public Shared Function SubS(ByVal value As String, ByVal start As Integer, ByVal length As Integer) As String  
        If value Is Nothing Then  
            Throw New ArgumentNullException("value")  
        End If  
  
        If length < 0 Then  
            Throw New ArgumentException("Invalid length parameter passed to the substring function.")  
        End If  
  
        ' In Transact-SQL, the substring method initializes to 1. So, start should be initialized to at least 1.  
        ' Length also has to be at least 1 or the Transact-SQL result would be an empty string.  
        If start + length <= 1 Then  
            Return String.Empty  
        End If  
  
        ' The 2 if statements below guarantee that the result will match the substring function in   
        ' Transact-SQL which will initialize start to 1 by subtracting from the length.  
        If start <= 0 AndAlso length > 0 Then  
            length -= 1  
        End If  
  
        If start <= 0 Then  
            length = length + start  
            start = 1  
        End If  
  
        Dim myIndex() As Integer  
        myIndex = StringInfo.ParseCombiningCharacters(value)  
  
        Dim NumOfIndexes As Integer  
        If (myIndex IsNot Nothing) Then  
            NumOfIndexes = myIndex.Length  
        Else  
            NumOfIndexes = 0  
        End If  
  
        start -= 1  
        If 0 <= start AndAlso start < NumOfIndexes Then  
            Dim lastIndex As Integer = start + length  
  
            ' if we are past the last char, then we get the string  
            ' up to the last char   
            If lastIndex > NumOfIndexes - 1 Then  
                Return value.Substring(myIndex(start))  
            Else  
                Return value.Substring(myIndex(start), myIndex(lastIndex) - myIndex(start))  
            End If  
        Else  
            Return String.Empty  
        End If  
    End Function  
  
    ''' <summary>  
    ''' LeftS is equal to T-SQL string function LEFT() which returns the left  
    ''' part of a character string with the specified number of characters.  
    ''' </summary>  
    ''' <param name="value">The input string.</param>  
    ''' <param name="length">The number of characters to return.</param>  
    ''' <returns>The string found at the starting position for n-length.</returns>  
    <Microsoft.SqlServer.Server.SqlFunction()> _  
    Public Shared Function LeftS(ByVal value As String, ByVal length As Integer) As String  
        If length < 0 Then  
            Throw New ArgumentException("Length must be a positive integer")  
        End If  
  
        Return SubS(value, 1, length)  
    End Function  
  
    ' RightS is equal to T-SQL string function RIGHT() which returns the right  
    '    part of a character string with the specified number of characters.  
    <Microsoft.SqlServer.Server.SqlFunction()> _  
    Public Shared Function RightS(ByVal value As String, ByVal length As Integer) As String  
        If value Is Nothing Then  
            Throw New ArgumentNullException("value")  
        End If  
  
        If length < 0 Then  
            Throw New NotSupportedException("Length must be a positive integer")  
        End If  
  
        Dim myIndex() As Integer  
  
        myIndex = StringInfo.ParseCombiningCharacters(value)  
        Dim NumOfIndexes As Integer  
        If (myIndex IsNot Nothing) Then  
            NumOfIndexes = myIndex.Length  
        Else  
            NumOfIndexes = 0  
        End If  
  
        If NumOfIndexes <= length Then  
            Return value  
        End If  
  
        If length = 0 Then  
            Return String.Empty  
        End If  
  
        Dim virtualStartIndex As Integer = NumOfIndexes - length  
        Dim physicalStartIndex As Integer = myIndex(virtualStartIndex)  
  
        Return value.Substring(physicalStartIndex)  
    End Function  
  
    ''' <summary>  
    ''' ReplaceS is equal to T-SQL string function REPLACE() which replaces all  
    ''' occurrences of the second given string expression in the first string expression  
    ''' with a third expression.  
    ''' </summary>  
    ''' <param name="value"></param>  
    ''' <param name="replaceValue"></param>  
    ''' <param name="newValue"></param>  
    ''' <returns></returns>  
    ''' <remarks></remarks>  
    <Microsoft.SqlServer.Server.SqlFunction()> _  
    Public Shared Function ReplaceS(ByVal value As String, ByVal replaceValue As String, ByVal newValue As String) As String  
        Dim result As New StringBuilder(value.Length)  
        Dim myIndex() As Integer  
        Dim i As Integer = 0  
        Dim upperValue As String = value.ToUpper(CultureInfo.CurrentUICulture)  
        Dim upperReplaceValue As String = replaceValue.ToUpper(CultureInfo.CurrentUICulture)  
  
        myIndex = StringInfo.ParseCombiningCharacters(upperValue)  
  
        While i < value.Length  
            Dim possibleMatch As Integer = upperValue.IndexOf(upperReplaceValue, i)  
            If possibleMatch < 0 Then  
                result.Append(value.Substring(i))  
                Exit While  
            Else  
                'Ensure we're not matching a partial surrogate  
                Dim surrogateIndex As Integer = Array.IndexOf(Of Integer)(myIndex, possibleMatch)  
                If surrogateIndex < 0 Then  
                    'We've matched in the middle of a surrogate, skip this match  
                    'as it is not valid.  
                    Dim nextStart As Integer = possibleMatch + 1  
                    result.Append(value.Substring(i, nextStart - i))  
                    i = nextStart  
                Else  
                    'This is a valid match.  Make the substitution.  
                    result.Append(value.Substring(i, possibleMatch - i))  
                    result.Append(newValue)  
                    i = possibleMatch + replaceValue.Length  
                End If  
            End If  
        End While  
  
        Return result.ToString()  
    End Function  
End Class  
```  
  
 <span data-ttu-id="b8729-138">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] インストール スクリプト (`Install.sql`) は、アセンブリを配置し、データベースに補助文字対応関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="b8729-138">This is the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation script (`Install.sql`), which deploys the assembly and creates the supplementary-aware functions in the database.</span></span>  
  
```  
Use [AdventureWorks]  
Go  
  
IF OBJECT_ID('[dbo].[len_s]') IS NOT NULL  
  DROP FUNCTION [dbo].[len_s];  
  
IF OBJECT_ID('[dbo].[sub_s]') IS NOT NULL  
  DROP FUNCTION [dbo].[sub_s];  
  
IF OBJECT_ID('[dbo].[left_s]') IS NOT NULL  
  DROP FUNCTION [dbo].[left_s];  
  
IF OBJECT_ID('[dbo].[right_s]') IS NOT NULL  
  DROP FUNCTION [dbo].[right_s];  
  
IF OBJECT_ID('[dbo].[replace_s]') IS NOT NULL  
  DROP FUNCTION [dbo].[replace_s];  
GO  
  
IF EXISTS (SELECT [name] FROM sys.assemblies  
             WHERE [name] = 'SurrogateStringFunction')  
  DROP ASSEMBLY SurrogateStringFunction;  
GO  
  
USE master  
GO  
  
IF EXISTS (SELECT * FROM sys.server_principals WHERE [name] = 'ExternalSample_Login')  
DROP LOGIN ExternalSample_Login;  
GO  
  
IF EXISTS (SELECT * FROM sys.asymmetric_keys WHERE [name] = 'ExternalSample_Key')  
DROP ASYMMETRIC KEY ExternalSample_Key;  
GO  
  
--Before we register the assembly to SQL Server, we must arrange for the appropriate permissions.  
--Assemblies with unsafe or external_access permissions can only be registered and operate correctly  
--if either the database trustworthy bit is set or if the assembly is signed with a key,  
--that key is registered with SQL Server, a server principal is created from that key,  
--and that principal is granted the external access or unsafe assembly permission.  We choose  
--the latter approach as it is more granular, and therefore safer.  You should never  
--register an assembly with SQL Server (especially with external_access or unsafe permissions) without  
--thoroughly reviewing the source code of the assembly to make sure that its actions   
--do not pose an operational or security risk for your site.  
  
DECLARE @SamplesPath nvarchar(1024);  
  
-- You may need to modify the value of the this variable if you have installed the sample someplace other than the default location.  
set @SamplesPath = N'C:\MySample\'  
  
EXEC('CREATE ASYMMETRIC KEY ExternalSample_Key FROM EXECUTABLE FILE = ''' + @SamplesPath   
    + 'SurrogateStringFunction.dll'';');  
CREATE LOGIN ExternalSample_Login FROM ASYMMETRIC KEY ExternalSample_Key  
GRANT EXTERNAL ACCESS ASSEMBLY TO ExternalSample_Login;  
GO  
  
USE AdventureWorks;  
GO  
  
--  
-- Create assembly to register class methods for create functions  
--   
DECLARE @SamplesPath nvarchar(1024);  
-- You may need to modify the value of the this variable if you have installed the sample someplace other than the default location.  
  
set @SamplesPath = N'C:\MySample\'  
  
CREATE ASSEMBLY [SurrogateStringFunction]  
FROM @SamplesPath + 'SurrogateStringFunction.dll'  
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
GO  
  
CREATE FUNCTION [dbo].[len_s] (@str nvarchar(4000))  
RETURNS bigint  
AS EXTERNAL NAME [SurrogateStringFunction].[SurrogateStringFunction].[LenS];  
GO  
  
CREATE FUNCTION [dbo].[sub_s](@str nvarchar(4000), @pos int, @cont int)  
RETURNS nvarchar(4000)  
AS EXTERNAL NAME [SurrogateStringFunction].[SurrogateStringFunction].[SubS];  
GO  
  
CREATE FUNCTION [dbo].[left_s](@str nvarchar(4000), @cont int)  
RETURNS nvarchar(4000)  
AS EXTERNAL NAME [SurrogateStringFunction].[SurrogateStringFunction].[LeftS];  
GO  
  
CREATE FUNCTION [dbo].[right_s](@str nvarchar(4000), @cont int)  
RETURNS nvarchar(4000)  
AS EXTERNAL NAME [SurrogateStringFunction].[SurrogateStringFunction].[RightS];  
GO  
  
CREATE FUNCTION [dbo].[replace_s](@str nvarchar(4000), @str1 nvarchar(4000), @str2 nvarchar(4000))  
RETURNS nvarchar(4000)  
AS EXTERNAL NAME [SurrogateStringFunction].[SurrogateStringFunction].[ReplaceS];  
GO  
```  
  
 <span data-ttu-id="b8729-139">次の `test.sql` は、関数を実行してサンプルをテストします。</span><span class="sxs-lookup"><span data-stu-id="b8729-139">This is `test.sql`, which tests the sample by executing the functions.</span></span>  
  
```  
Use [AdventureWorks]  
Go  
  
-- left_s  VS  Left  
print ('***** left_s VS Left *****');  
select [dbo].[left_s](N'𠱷𠱸123',2);  
print(N'Should Return 𠱷𠱸');  
go  
select Left(N'𠱷𠱸123',2);  
print(N'Will Return 𠱷');  
go  
  
-- right_s VS Right  
print ('***** right_s VS Right *****')  
select [dbo].[right_s](N'𠱷𠱸123',5);  
print(N'Should Return 𠱷𠱸123');  
go  
select Right(N'𠱷𠱸123',5);  
print(N'Will Return 𠱸123');  
go  
  
-- len_s  VS Len  
print('***** len_s VS Len *****');  
select [dbo].[len_s](N'𠆾𠇀𠇃12');  
print(N'Should Return 5');  
go  
select Len(N'𠆾𠇀𠇃12');  
print(N'Will Return 8');  
go  
  
-- sub_s VS Substring  
print('***** sub_s VS Subscription *****');  
select [dbo].[sub_s] (N'𢙢𢙣𢙤𢙥𢙦𢙧𢙨𢙩𢙪𢙫𢙬𢙭𢙮𢙯𢙰𢙱𢙲𢙳',3,5);  
print(N'Should Return 𢙤𢙥𢙦𢙧𢙨');  
go  
select substring(N'𢙢𢙣𢙤𢙥𢙦𢙧𢙨𢙩𢙪𢙫𢙬𢙭𢙮𢙯𢙰𢙱𢙲𢙳',3,5);  
print(N'Will Return 𢙣𢙤');  
go  
  
-- replace_s VS Replace  
print('***** replace_s VS Replace *****');  
select [dbo].[replace_s](N'𡥕𡥖𡥗𡥙𡥚𡥛𡥕𡥖𡥗𡥙𡥚𡥛',N'𡥗𡥙𡥚',N'𡦼');  
print(N'Should Return 𡥖𡦼𡥛𡥕𡥖𡦼𡥛');  
go  
select replace(N'𡥕𡥖𡥗𡥙𡥚𡥛𡥕𡥖𡥗𡥙𡥚𡥛',N'𡥗𡥙𡥚',N'𡦼');  
print(N'Will Return 𡦼');  
go  
```  
  
 <span data-ttu-id="b8729-140">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] は、アセンブリと関数をデータベースから削除します。</span><span class="sxs-lookup"><span data-stu-id="b8729-140">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] removes the assembly and functions from the database.</span></span>  
  
```  
-- Drop assemblies and functions if they exist.  
USE [AdventureWorks]  
GO  
  
IF OBJECT_ID('[dbo].[len_s]') IS NOT NULL  
  DROP FUNCTION [dbo].[len_s];  
  
IF OBJECT_ID('[dbo].[sub_s]') IS NOT NULL  
  DROP FUNCTION [dbo].[sub_s];  
  
IF OBJECT_ID('[dbo].[left_s]') IS NOT NULL  
  DROP FUNCTION [dbo].[left_s];  
  
IF OBJECT_ID('[dbo].[right_s]') IS NOT NULL  
  DROP FUNCTION [dbo].[right_s];  
  
IF OBJECT_ID('[dbo].[replace_s]') IS NOT NULL  
  DROP FUNCTION [dbo].[replace_s];  
GO  
  
IF EXISTS (SELECT [name] FROM sys.assemblies  
             WHERE [name] = 'SurrogateStringFunction')  
  DROP ASSEMBLY SurrogateStringFunction;  
GO  
  
USE master  
GO  
  
IF EXISTS (SELECT * FROM sys.server_principals WHERE [name] = 'ExternalSample_Login')  
DROP LOGIN ExternalSample_Login;  
GO  
  
IF EXISTS (SELECT * FROM sys.asymmetric_keys WHERE [name] = 'ExternalSample_Key')  
DROP ASYMMETRIC KEY ExternalSample_Key;  
GO  
  
USE [AdventureWorks]  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8729-141">参照</span><span class="sxs-lookup"><span data-stu-id="b8729-141">See Also</span></span>  
 [<span data-ttu-id="b8729-142">CLR &#40;共通言語ランタイム&#41; 統合の使用シナリオと例</span><span class="sxs-lookup"><span data-stu-id="b8729-142">Usage Scenarios and Examples for Common Language Runtime &#40;CLR&#41; Integration</span></span>](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  

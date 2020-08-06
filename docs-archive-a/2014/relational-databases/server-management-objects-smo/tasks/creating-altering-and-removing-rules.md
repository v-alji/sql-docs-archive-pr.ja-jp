---
title: ルールの作成、変更、および削除 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- rules [SMO]
ms.assetid: 16981459-524e-4b39-a899-4370eaf763cc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7742a9cb718bdde4f268d5226c45eba475f44ddd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643219"
---
# <a name="creating-altering-and-removing-rules"></a><span data-ttu-id="cac46-102">ルールの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="cac46-102">Creating, Altering, and Removing Rules</span></span>
  <span data-ttu-id="cac46-103">SMO では、<xref:Microsoft.SqlServer.Management.Smo.Rule> オブジェクトでルールが表現されます。</span><span class="sxs-lookup"><span data-stu-id="cac46-103">In SMO, rules are represented by the <xref:Microsoft.SqlServer.Management.Smo.Rule> object.</span></span> <span data-ttu-id="cac46-104">ルールは、<xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> プロパティによって定義されます。このプロパティは、IN、LIKE、または BETWEEN などの演算子や述語を使用した条件式を格納したテキスト文字列です。</span><span class="sxs-lookup"><span data-stu-id="cac46-104">The rule is defined by the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> property, which is a text string that contains a condition expression that uses operators or predicates, such as IN, LIKE, or BETWEEN.</span></span> <span data-ttu-id="cac46-105">ルールでは、列や別のデータベース オブジェクトを参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="cac46-105">A rule cannot reference columns or other database objects.</span></span> <span data-ttu-id="cac46-106">データベース オブジェクトを参照しない組み込み関数は含めることができます。</span><span class="sxs-lookup"><span data-stu-id="cac46-106">Built-in functions that do not reference database objects can be included.</span></span>  
  
 <span data-ttu-id="cac46-107"><xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> プロパティでの定義には、入力されたデータ値を参照する変数が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cac46-107">The definition in the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> property must contain a variable that refers to the data value entered.</span></span> <span data-ttu-id="cac46-108">ルールを作成するときに、任意の名前または記号を使用して値を表すことができますが、最初の文字は記号である必要があり \@ ます。</span><span class="sxs-lookup"><span data-stu-id="cac46-108">Any name or symbol can be used to represent the value when creating the rule, but the first character must be the \@ symbol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cac46-109">例</span><span class="sxs-lookup"><span data-stu-id="cac46-109">Example</span></span>  
 <span data-ttu-id="cac46-110">提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cac46-110">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="cac46-111">詳細については、「 [Visual studio .net で VISUAL BASIC SMO プロジェクトを作成する](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)」または「visual [Studio .Net で VISUAL C&#35; Smo プロジェクトを作成](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cac46-111">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-altering-and-removing-a-rule-in-visual-basic"></a><span data-ttu-id="cac46-112">Visual Basic でのルールの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="cac46-112">Creating, Altering, and Removing a Rule in Visual Basic</span></span>  
 <span data-ttu-id="cac46-113">このコード例では、ルールの作成、作成したルールの列へのアタッチ、<xref:Microsoft.SqlServer.Management.Smo.Rule> オブジェクトのプロパティの修正、列からのデタッチ、および削除を行う方法を示します。</span><span class="sxs-lookup"><span data-stu-id="cac46-113">This code sample shows how to create a rule, attach it to a column, modify properties of the <xref:Microsoft.SqlServer.Management.Smo.Rule> object, detach it from the column, and then drop it.</span></span>  
  
 <span data-ttu-id="cac46-114"><xref:Microsoft.SqlServer.Management.Smo.Rule> オブジェクトの `Dim` ステートメントを完全なアセンブリ パスで指定して、System.Data アセンブリの <xref:Microsoft.SqlServer.Management.Smo.Rule> オブジェクトと明確に区別します。</span><span class="sxs-lookup"><span data-stu-id="cac46-114">The `Dim` statement for the <xref:Microsoft.SqlServer.Management.Smo.Rule> object is specified with the full assembly path to avoid ambiguity with a <xref:Microsoft.SqlServer.Management.Smo.Rule> object in the System.Data assembly.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBRules1](SMO How to#SMO_VBRules1)]  -->  
  
## <a name="creating-altering-and-removing-a-rule-in-visual-c"></a><span data-ttu-id="cac46-115">Visual C# でのルールの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="cac46-115">Creating, Altering, and Removing a Rule in Visual C#</span></span>  
 <span data-ttu-id="cac46-116">このコード例では、ルールの作成、作成したルールの列へのアタッチ、<xref:Microsoft.SqlServer.Management.Smo.Rule> オブジェクトのプロパティの修正、列からのデタッチ、および削除を行う方法を示します。</span><span class="sxs-lookup"><span data-stu-id="cac46-116">This code sample shows how to create a rule, attach it to a column, modify properties of the <xref:Microsoft.SqlServer.Management.Smo.Rule> object, detach it from the column, and then drop it.</span></span>  
  
 <span data-ttu-id="cac46-117"><xref:Microsoft.SqlServer.Management.Smo.Rule> オブジェクトの `Dim` ステートメントを完全なアセンブリ パスで指定して、System.Data アセンブリの <xref:Microsoft.SqlServer.Management.Smo.Rule> オブジェクトと明確に区別します。</span><span class="sxs-lookup"><span data-stu-id="cac46-117">The `Dim` statement for the <xref:Microsoft.SqlServer.Management.Smo.Rule> object is specified with the full assembly path to avoid ambiguity with a <xref:Microsoft.SqlServer.Management.Smo.Rule> object in the System.Data assembly.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Rule object variable by supplying the parent database, name and schema in the constructor.   
            //Note that the full namespace must be given for the Rule type to differentiate it from other Rule types.   
            Microsoft.SqlServer.Management.Smo.Rule ru;  
            ru = new Rule(db, "TestRule", "Production");  
            //Set the TextHeader and TextBody properties to define the rule.   
            ru.TextHeader = "CREATE RULE [Production].[TestRule] AS";  
            ru.TextBody = "@value BETWEEN GETDATE() AND DATEADD(year,4,GETDATE())";  
            //Create the rule on the instance of SQL Server.   
            ru.Create();  
            //Bind the rule to a column in the Product table by supplying the table, schema, and   
            //column as arguments in the BindToColumn method.   
            ru.BindToColumn("Product", "SellEndDate", "Production");  
            //Unbind from the column before removing the rule from the database.   
            ru.UnbindFromColumn("Product", "SellEndDate", "Production");  
            ru.Drop();  
  
        }  
```  
  
## <a name="creating-altering-and-removing-a-rule-in-powershell"></a><span data-ttu-id="cac46-118">PowerShell でのルールの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="cac46-118">Creating, Altering, and Removing a Rule in PowerShell</span></span>  
 <span data-ttu-id="cac46-119">このコード例では、ルールの作成、作成したルールの列へのアタッチ、<xref:Microsoft.SqlServer.Management.Smo.Rule> オブジェクトのプロパティの修正、列からのデタッチ、および削除を行う方法を示します。</span><span class="sxs-lookup"><span data-stu-id="cac46-119">This code sample shows how to create a rule, attach it to a column, modify properties of the <xref:Microsoft.SqlServer.Management.Smo.Rule> object, detach it from the column, and then drop it.</span></span>  
  
 <span data-ttu-id="cac46-120"><xref:Microsoft.SqlServer.Management.Smo.Rule> オブジェクトの `Dim` ステートメントを完全なアセンブリ パスで指定して、System.Data アセンブリの <xref:Microsoft.SqlServer.Management.Smo.Rule> オブジェクトと明確に区別します。</span><span class="sxs-lookup"><span data-stu-id="cac46-120">The `Dim` statement for the <xref:Microsoft.SqlServer.Management.Smo.Rule> object is specified with the full assembly path to avoid ambiguity with a <xref:Microsoft.SqlServer.Management.Smo.Rule> object in the System.Data assembly.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
# Define a Rule object variable by supplying the parent database, name and schema in the constructor.
$ru = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Rule -argumentlist $db, "TestRule", "Production"  
  
#Set the TextHeader and TextBody properties to define the rule.
$ru.TextHeader = "CREATE RULE [Production].[TestRule] AS"  
$ru.TextBody = "@value BETWEEN GETDATE() AND DATEADD(year,4,GETDATE())"  
  
#Create the rule on the instance of SQL Server.
$ru.Create()  
  
# Bind the rule to a column in the Product table by supplying the table, schema, and column as arguments in the BindToColumn method.
$ru.BindToColumn("Product", "SellEndDate", "Production")  
  
#Unbind from the column before removing the rule from the database.
$ru.UnbindFromColumn("Product", "SellEndDate", "Production")  
$ru.Drop()  
```  
  
## <a name="see-also"></a><span data-ttu-id="cac46-121">参照</span><span class="sxs-lookup"><span data-stu-id="cac46-121">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Rule>  

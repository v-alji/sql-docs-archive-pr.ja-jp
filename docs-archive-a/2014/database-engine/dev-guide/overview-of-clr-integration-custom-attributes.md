---
title: CLR 統合のカスタム属性の概要 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- custom attributes [CLR integration]
- attributes [CLR integration]
- common language runtime [SQL Server], attributes
- database objects [CLR integration], custom attributes
- building database objects [CLR integration], custom attributes
ms.assetid: ecf5c097-0972-48e2-a9c0-b695b7dd2820
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: aa0bf94ee27fd89a6aa690e0ff2f8e3295648946
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632087"
---
# <a name="overview-of-clr-integration-custom-attributes"></a><span data-ttu-id="be0a5-102">CLR 統合のカスタム属性の概要</span><span class="sxs-lookup"><span data-stu-id="be0a5-102">Overview of CLR Integration Custom Attributes</span></span>
  <span data-ttu-id="be0a5-103">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] の CLR (共通言語ランタイム) では、属性という説明用のキーワードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="be0a5-103">The common language runtime (CLR) of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] allows the use of descriptive keywords, called attributes.</span></span> <span data-ttu-id="be0a5-104">これらの属性は、メソッドやクラスなどの多くの要素に関する追加情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="be0a5-104">These attributes provide additional information for many elements, such as methods and classes.</span></span> <span data-ttu-id="be0a5-105">属性はオブジェクトのメタデータと共にアセンブリに保存され、記述したコードを他の開発ツールに説明したり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内部での実行時の動作に影響することを説明するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="be0a5-105">The attributes are saved in the assembly with the metadata of the object, and can be used to describe your code to other development tools or to affect runtime behavior inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="be0a5-106">CLR ルーチンを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に登録すると、そのルーチンに関する一連のプロパティが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により抽出されます。</span><span class="sxs-lookup"><span data-stu-id="be0a5-106">When you register a CLR routine with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] derives a set of properties about the routine.</span></span> <span data-ttu-id="be0a5-107">これらのプロパティによって、ルーチンにインデックスを作成できるかどうかなど、そのルーチンの機能が決まります。</span><span class="sxs-lookup"><span data-stu-id="be0a5-107">These routine properties determine the capabilities of the routine, including whether the routine can be indexed.</span></span> <span data-ttu-id="be0a5-108">たとえば、`DataAccess` プロパティを `DataAccessKind.Read` に設定すると、CLR 関数内から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザー テーブルのデータにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="be0a5-108">For example, setting the `DataAccess` property to `DataAccessKind.Read` lets you access data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user tables inside a CLR function.</span></span> <span data-ttu-id="be0a5-109">次の例は、 `DataAccess` ユーザーテーブル**table1**からのデータアクセスを容易にするために、プロパティが設定されている単純なケースを示しています。</span><span class="sxs-lookup"><span data-stu-id="be0a5-109">The following example shows a simple case in which the `DataAccess` property is set to facilitate data access from a user table **table1**.</span></span>  
  
```csharp  
using System;  
using System.Data;  
using System.Data.Sql;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
  
public partial class UserDefinedFunctions  
{  
    [SqlFunction(DataAccess = DataAccessKind.Read)]  
    public static string func1()  
    {  
        // Open a connection and create a command  
        SqlConnection conn = new SqlConnection("context connection = true");  
        conn.Open();  
        SqlCommand cmd = conn.CreateCommand();  
        cmd.CommandText = "SELECT str_val FROM table1 WHERE int_val = 10";  
        // where table1 is a user table  
        // Execute this command   
        SqlDataReader rd = cmd.ExecuteReader();  
        // Set string ret_val to str_val returned from the query  
        string ret_val = rd.GetValue(0).ToString();  
        rd.Close();  
        return ret_val;  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
Public partial Class UserDefinedFunctions  
    <SqlFunction(DataAccess = DataAccessKind.Read)> _   
    Public Shared Function func1() As String  
        ' Open a connection and create a command  
        Dim conn As SqlConnection = New SqlConnection("context connection = true")   
        conn.Open()  
        Dim cmd As SqlCommand =  conn.CreateCommand()   
        cmd.CommandText = "SELECT str_val FROM table1 WHERE int_val = 10"  
        ' where table1 is a user table  
        ' Execute this command   
        Dim rd As SqlDataReader =  cmd.ExecuteReader()   
        ' Set string ret_val to str_val returned from the query  
        Dim ret_val As String =  rd.GetValue(0).ToString()   
        rd.Close()  
        Return ret_val  
    End Function  
End Class  
```  
  
 <span data-ttu-id="be0a5-110">[!INCLUDE[tsql](../../includes/tsql-md.md)] ルーチンの場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により、ルーチン定義から直接ルーチンのプロパティが抽出されます。</span><span class="sxs-lookup"><span data-stu-id="be0a5-110">For [!INCLUDE[tsql](../../includes/tsql-md.md)] routines, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] derives routine properties directly from the routine definition.</span></span> <span data-ttu-id="be0a5-111">CLR ルーチンの場合は、これらのプロパティを抽出するときに、サーバーでルーチン本体が分析されません。</span><span class="sxs-lookup"><span data-stu-id="be0a5-111">For CLR routines, the server does not analyze the body of the routine to derive these properties.</span></span> <span data-ttu-id="be0a5-112">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 言語で実装されているクラスとクラスのメンバーには、カスタム属性を使用できます。</span><span class="sxs-lookup"><span data-stu-id="be0a5-112">Instead, you can use custom attributes for classes and class members implemented in a [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] language.</span></span>  
  
 <span data-ttu-id="be0a5-113">CLR ルーチン、ユーザー定義型、およびユーザー定義集計に必要なカスタム属性は、`Microsoft.SqlServer.Server` 名前空間で定義します。</span><span class="sxs-lookup"><span data-stu-id="be0a5-113">The custom attributes needed for CLR routines, user-defined types, and aggregates are defined in the `Microsoft.SqlServer.Server` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be0a5-114">参照</span><span class="sxs-lookup"><span data-stu-id="be0a5-114">See Also</span></span>  
 [<span data-ttu-id="be0a5-115">CLR ルーチンのカスタム属性</span><span class="sxs-lookup"><span data-stu-id="be0a5-115">Custom Attributes for CLR Routines</span></span>](../../relational-databases/clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md)  
  
  

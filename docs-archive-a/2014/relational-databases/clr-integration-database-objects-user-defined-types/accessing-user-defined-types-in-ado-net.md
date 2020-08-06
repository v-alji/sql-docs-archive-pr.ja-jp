---
title: ADO.NET | でのユーザー定義型へのアクセスMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- UDTs [CLR integration], ADO.NET
- user-defined types [CLR integration], ADO.NET
ms.assetid: 4b0d876c-8066-490e-8e18-327c0e942b19
author: rothja
ms.author: jroth
ms.openlocfilehash: a94e333ad743ed07dff6b973ebfe227312a1cab2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643408"
---
# <a name="accessing-user-defined-types-in-adonet"></a><span data-ttu-id="6191b-102">ADO.NET でのユーザー定義型へのアクセス</span><span class="sxs-lookup"><span data-stu-id="6191b-102">Accessing User-Defined Types in ADO.NET</span></span>
  <span data-ttu-id="6191b-103">ユーザー定義型 (Udt) は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 検証可能なコードを生成する .NET Framework 共通言語ランタイム (CLR) でサポートされている言語のいずれかを使用して記述されます。</span><span class="sxs-lookup"><span data-stu-id="6191b-103">User-defined types (UDTs) are written using any of the languages supported by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework common language runtime (CLR) that produce verifiable code.</span></span> <span data-ttu-id="6191b-104">サポートされる言語には、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# や [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic などがあります。</span><span class="sxs-lookup"><span data-stu-id="6191b-104">This includes [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic.</span></span> <span data-ttu-id="6191b-105">UDT では、オブジェクトやカスタム データ構造を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに格納できます。</span><span class="sxs-lookup"><span data-stu-id="6191b-105">UDTs allow objects and custom data structures to be stored in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="6191b-106">データは、.NET Framework のクラスまたは構造体のパブリック メンバーとして公開され、動作は .NET Framework のクラスまたは構造体のメソッドによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="6191b-106">The data is exposed as public members of a .NET Framework class or structure, and behaviors are defined by methods of the class or structure.</span></span> <span data-ttu-id="6191b-107">UDT は、テーブルの列定義、[!INCLUDE[tsql](../../includes/tsql-md.md)] バッチの変数、または [!INCLUDE[tsql](../../includes/tsql-md.md)] 関数やストアド プロシージャの引数として使用することができます。</span><span class="sxs-lookup"><span data-stu-id="6191b-107">A UDT can be used as the column definition of a table, as a variable in a [!INCLUDE[tsql](../../includes/tsql-md.md)] batch, or as an argument of a [!INCLUDE[tsql](../../includes/tsql-md.md)] function or stored procedure.</span></span>  
  
 <span data-ttu-id="6191b-108">ADO.NET では、`System.Data.SqlClient` プロバイダーにより次の形態で UDT が公開されます。</span><span class="sxs-lookup"><span data-stu-id="6191b-108">In ADO.NET, the `System.Data.SqlClient` provider exposes UDTs in the following ways:</span></span>  
  
-   <span data-ttu-id="6191b-109">`System.Data.SqlClient.SqlDataReader` によりオブジェクトとして。</span><span class="sxs-lookup"><span data-stu-id="6191b-109">Through the `System.Data.SqlClient.SqlDataReader` as an object.</span></span>  
  
-   <span data-ttu-id="6191b-110">`SqlDataReader` により生のバイト列として。</span><span class="sxs-lookup"><span data-stu-id="6191b-110">Through the `SqlDataReader` as raw bytes.</span></span>  
  
-   <span data-ttu-id="6191b-111">`System.Data.SqlClient.SqlParameter` オブジェクトのパラメーターとして。</span><span class="sxs-lookup"><span data-stu-id="6191b-111">As a parameter of a `System.Data.SqlClient.SqlParameter` object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6191b-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="6191b-112">In This Section</span></span>  
 [<span data-ttu-id="6191b-113">UDT データの取得</span><span class="sxs-lookup"><span data-stu-id="6191b-113">Retrieving UDT Data</span></span>](accessing-user-defined-types-retrieving-udt-data.md)  
 <span data-ttu-id="6191b-114">UDT データを取得する方法とパラメーターを指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6191b-114">Describes how to retrieve UDT data and how to specify parameters.</span></span>  
  
 [<span data-ttu-id="6191b-115">データ アダプターによる UDT 列の更新</span><span class="sxs-lookup"><span data-stu-id="6191b-115">Updating UDT Columns with DataAdapters</span></span>](accessing-user-defined-types-updating-udt-columns-with-dataadapters.md)  
 <span data-ttu-id="6191b-116">`DataSets` 内の UDT を操作する方法と `DataAdapters` を使用して UDT データを更新する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6191b-116">Describes how to work with UDTs in `DataSets` and how to update UDT data using `DataAdapters`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6191b-117">参照</span><span class="sxs-lookup"><span data-stu-id="6191b-117">See Also</span></span>  
 [<span data-ttu-id="6191b-118">CLR ユーザー定義型</span><span class="sxs-lookup"><span data-stu-id="6191b-118">CLR User-Defined Types</span></span>](clr-user-defined-types.md)  
  
  

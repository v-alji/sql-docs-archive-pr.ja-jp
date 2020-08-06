---
title: データ型の操作 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- DataType object
- SQL Server Management Objects, data types
- data types [SMO]
- SMO [SQL Server], data types
ms.assetid: 1e0e736a-c709-4d89-aeb2-b32dcfd641fa
author: stevestein
ms.author: sstein
ms.openlocfilehash: cbffc1c59eb12fa0f448a7fcb26157d5e18dba3f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633014"
---
# <a name="working-with-data-types"></a><span data-ttu-id="96e10-102">データ型の処理</span><span class="sxs-lookup"><span data-stu-id="96e10-102">Working with Data Types</span></span>
  <span data-ttu-id="96e10-103">データは、定義済みの長さを持つ文字列、特定の精度を持つ数値、または独自のルール セットを持つ別のオブジェクトであるユーザー定義データ型など、さまざまな型およびサイズで表現されます。</span><span class="sxs-lookup"><span data-stu-id="96e10-103">Data comes in many types and sizes, such as a string that has a defined length, a number that has specific accuracy, or a user-defined data type that is another object that has its own set of rules.</span></span> <span data-ttu-id="96e10-104">オブジェクトは、 <xref:Microsoft.SqlServer.Management.Smo.DataType> によって適切に処理できるように、データの型を分類し [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="96e10-104">The <xref:Microsoft.SqlServer.Management.Smo.DataType> object classifies the type of data so that it can be handled correctly by [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="96e10-105"><xref:Microsoft.SqlServer.Management.Smo.DataType> オブジェクトは、データを受け入れるオブジェクトに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="96e10-105">The <xref:Microsoft.SqlServer.Management.Smo.DataType> object is associated with objects that accept data.</span></span> <span data-ttu-id="96e10-106">次の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) オブジェクトに渡すデータは、<xref:Microsoft.SqlServer.Management.Smo.DataType> オブジェクト プロパティによって定義されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="96e10-106">The following [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) objects accept data that must be defined by a <xref:Microsoft.SqlServer.Management.Smo.DataType> object property:</span></span>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Column>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedAggregateParameter>  
  
 <span data-ttu-id="96e10-107">データを受け入れるオブジェクトの `DataType` プロパティは、次のいくつかの方法で設定することができます。</span><span class="sxs-lookup"><span data-stu-id="96e10-107">The `DataType` property for objects that accept data can be set in several ways.</span></span>  
  
-   <span data-ttu-id="96e10-108">既定のコンストラクターを使用して、<xref:Microsoft.SqlServer.Management.Smo.DataType> オブジェクト プロパティを明示的に指定する。</span><span class="sxs-lookup"><span data-stu-id="96e10-108">Use the default constructor and specify <xref:Microsoft.SqlServer.Management.Smo.DataType> object properties explicitly</span></span>  
  
-   <span data-ttu-id="96e10-109">オーバーロードされたコンストラクターを使用して、<xref:Microsoft.SqlServer.Management.Smo.DataType> プロパティをパラメーターとして指定する。</span><span class="sxs-lookup"><span data-stu-id="96e10-109">Use an overloaded constructor and specify the <xref:Microsoft.SqlServer.Management.Smo.DataType> properties as parameters.</span></span>  
  
-   <span data-ttu-id="96e10-110">オブジェクト コンストラクター内で <xref:Microsoft.SqlServer.Management.Smo.DataType> インラインを指定する。</span><span class="sxs-lookup"><span data-stu-id="96e10-110">Specify the <xref:Microsoft.SqlServer.Management.Smo.DataType> inline in the object constructor.</span></span>  
  
-   <span data-ttu-id="96e10-111">`Int` など、<xref:Microsoft.SqlServer.Management.Smo.DataType> クラスの静的メンバーの 1 つを使用する。</span><span class="sxs-lookup"><span data-stu-id="96e10-111">Use one of the static members of the <xref:Microsoft.SqlServer.Management.Smo.DataType> class, for example `Int`.</span></span> <span data-ttu-id="96e10-112">これによって、実際に <xref:Microsoft.SqlServer.Management.Smo.DataType> オブジェクトのインスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="96e10-112">This will in fact return an instance of a <xref:Microsoft.SqlServer.Management.Smo.DataType> object.</span></span>  
  
 <span data-ttu-id="96e10-113"><xref:Microsoft.SqlServer.Management.Smo.DataType> オブジェクトには、データの型を定義するいくつかのプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="96e10-113">The <xref:Microsoft.SqlServer.Management.Smo.DataType> object has several properties that define the type of data.</span></span> <span data-ttu-id="96e10-114">たとえば、<xref:Microsoft.SqlServer.Management.Smo.SqlDataType> プロパティは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="96e10-114">For example, the <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> property specifies the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type.</span></span> <span data-ttu-id="96e10-115">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型を表す定数値は <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> 列挙にリストされます。</span><span class="sxs-lookup"><span data-stu-id="96e10-115">The constant values that represent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types are listed in the <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> enumeration.</span></span> <span data-ttu-id="96e10-116">これは、`varchar`、`nchar`、`currency`、`integer`、`float`、および `datetime` などのデータ型を参照します。</span><span class="sxs-lookup"><span data-stu-id="96e10-116">This refers to data types such as `varchar`, `nchar`, `currency`, `integer`, `float`, and `datetime`.</span></span>  
  
 <span data-ttu-id="96e10-117">データ型を確立したら、そのデータに対して特定のプロパティを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="96e10-117">When the data type is established, specific properties must be set for the data.</span></span> <span data-ttu-id="96e10-118">たとえば、`nchar` 型の場合、`Length` プロパティで文字列データの長さを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="96e10-118">For example, if it is an `nchar` type, the length of the string data must be set in the `Length` property.</span></span> <span data-ttu-id="96e10-119">これは、有効桁数と小数点以下桁数を指定する必要のある数値に対しても同様です。</span><span class="sxs-lookup"><span data-stu-id="96e10-119">The same applies for numeric values, where you would have to specify precision and scale.</span></span>  
  
 <span data-ttu-id="96e10-120"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> データ型および <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> データ型は、ユーザーによって定義されるデータの型の定義を含んでいるオブジェクトを参照します。</span><span class="sxs-lookup"><span data-stu-id="96e10-120"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> and <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> data types refer to objects that contain the definition of the type of data defined by the user.</span></span> <span data-ttu-id="96e10-121"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> は、<xref:Microsoft.SqlServer.Management.Smo.SqlDataType> 列挙からの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型に基づいています。</span><span class="sxs-lookup"><span data-stu-id="96e10-121">The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> is based on [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types from the <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> enumeration.</span></span> <span data-ttu-id="96e10-122"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>は .net のデータ型に基づいてい [!INCLUDE[msCoName](../../../includes/msconame-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="96e10-122">The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> is based on [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET data types.</span></span> <span data-ttu-id="96e10-123">これらは、組織で定義されているビジネス ルールに従ってデータベースで頻繁に再利用される型のデータを表現していることが普通です。</span><span class="sxs-lookup"><span data-stu-id="96e10-123">Typically, these would represent data of a specific type that is frequently reused by the database because of business rules defined by the organization.</span></span> <span data-ttu-id="96e10-124">たとえば、複数の通貨を扱う会社では、金額や通貨基準を格納するデータ型が役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="96e10-124">For example, a data type that stores an amount of money and a currency denominator would be helpful in a company that deals in multiple currencies.</span></span>  
  
 <span data-ttu-id="96e10-125"><xref:Microsoft.SqlServer.Management.Smo.SqlDataType> 列挙には、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] がサポートするすべてのデータ型のリストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="96e10-125">The <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> enumeration contains a list of all the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-supported data types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="96e10-126">例</span><span class="sxs-lookup"><span data-stu-id="96e10-126">Examples</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="constructing-a-datatype-object-with-the-specification-in-the-constructor-in-visual-basic"></a><span data-ttu-id="96e10-127">Visual Basic でのコンストラクター内の指定による DataType オブジェクトの構築</span><span class="sxs-lookup"><span data-stu-id="96e10-127">Constructing a DataType Object with the Specification in the Constructor in Visual Basic</span></span>  
 <span data-ttu-id="96e10-128">このコード例では、コンストラクターを使用して各種の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型に基づいたデータ型のインスタンスを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="96e10-128">This code example shows how to use the constructor to create instances of data types that are based on different [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="96e10-129"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>、<xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>、および XML 型にはすべて、オブジェクトを識別するための名前の値が必要です。</span><span class="sxs-lookup"><span data-stu-id="96e10-129">The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>, and XML types all require a name value to identify the object.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDataTypes1](SMO How to#SMO_VBDataTypes1)]  -->  
  
## <a name="constructing-a-datatype-object-with-the-specification-in-the-constructor-in-visual-c"></a><span data-ttu-id="96e10-130">Visual C# でのコンストラクター内の指定による DataType オブジェクトの構築</span><span class="sxs-lookup"><span data-stu-id="96e10-130">Constructing a DataType Object with the Specification in the Constructor in Visual C#</span></span>  
 <span data-ttu-id="96e10-131">このコード例では、コンストラクターを使用して各種の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型に基づいたデータ型のインスタンスを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="96e10-131">This code example shows how to use the constructor to create instances of data types that are based on different [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="96e10-132"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>、<xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>、および XML 型にはすべて、オブジェクトを識別するための名前の値が必要です。</span><span class="sxs-lookup"><span data-stu-id="96e10-132">The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>, and XML types all require a name value to identify the object.</span></span>  
  
```  
{   
//Declare a DataType object variable and define the data type in the constructor.   
DataType dt;   
//For the decimal data type the following two arguments specify precision, and scale.   
dt = new DataType(SqlDataType.Decimal, 10, 2);   
}  
```  
  
## <a name="constructing-a-datatype-object-by-using-the-default-constructor-in-visual-basic"></a><span data-ttu-id="96e10-133">Visual Basic での既定のコンストラクターを使用した DataType オブジェクトの構築</span><span class="sxs-lookup"><span data-stu-id="96e10-133">Constructing a DataType Object by Using the Default Constructor in Visual Basic</span></span>  
 <span data-ttu-id="96e10-134">このコード例では、既定のコンストラクターを使用して各種の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型に基づいたデータ型のインスタンスを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="96e10-134">This code example shows how to use the default constructor to create instances of data types that are based on different [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types.</span></span> <span data-ttu-id="96e10-135">データ型の指定にはプロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="96e10-135">The properties are then used to specify the data type.</span></span>  
  
 <span data-ttu-id="96e10-136">**メモ**<xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>、 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> 、および XML 型にはすべて、オブジェクトを識別するための名前値が必要です。</span><span class="sxs-lookup"><span data-stu-id="96e10-136">**Note** The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>, and XML types all require a name value to identify the object.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDataTypes2](SMO How to#SMO_VBDataTypes2)]  -->  
  
## <a name="constructing-a-datatype-object-by-using-the-default-constructor-in-visual-c"></a><span data-ttu-id="96e10-137">Visual C# での既定のコンストラクターを使用した DataType オブジェクトの構築</span><span class="sxs-lookup"><span data-stu-id="96e10-137">Constructing a DataType Object by Using the Default Constructor in Visual C#</span></span>  
 <span data-ttu-id="96e10-138">このコード例では、既定のコンストラクターを使用して各種の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型に基づいたデータ型のインスタンスを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="96e10-138">This code example shows how to use the default constructor to create instances of data types that are based on different [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types.</span></span> <span data-ttu-id="96e10-139">データ型の指定にはプロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="96e10-139">The properties are then used to specify the data type.</span></span>  
  
 <span data-ttu-id="96e10-140">**メモ**<xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>、 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> 、および XML 型にはすべて、オブジェクトを識別するための名前値が必要です。</span><span class="sxs-lookup"><span data-stu-id="96e10-140">**Note** The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>, and XML types all require a name value to identify the object.</span></span>  
  
```  
{   
//Declare and create a DataType object variable.   
DataType dt;   
dt = new DataType();   
//Define the data type by setting the SqlDataType property.   
dt.SqlDataType = SqlDataType.VarChar;   
//The VarChar data type requires a value for the MaximumLength property.   
dt.MaximumLength = 100;   
}  
```  
  
  

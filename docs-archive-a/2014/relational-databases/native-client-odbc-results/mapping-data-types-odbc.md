---
title: データ型のマッピング (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- mapping data types [ODBC]
- result sets [ODBC], data types
- ODBC data types, mapping
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- data types [ODBC], mapping
- sql_variant data type
- SQL Server Native Client ODBC driver, data types
ms.assetid: 4ba0924d-9fca-4c48-aced-0a8d817b3dde
author: rothja
ms.author: jroth
ms.openlocfilehash: 545e738afb6b3283b2ff2f3830921da8ed13202f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741974"
---
# <a name="mapping-data-types-odbc"></a><span data-ttu-id="a4fa2-102">データ型のマッピング (ODBC)</span><span class="sxs-lookup"><span data-stu-id="a4fa2-102">Mapping Data Types (ODBC)</span></span>
  <span data-ttu-id="a4fa2-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT odbc ドライバーでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sql データ型が odbc sql データ型にマップされます。</span><span class="sxs-lookup"><span data-stu-id="a4fa2-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver maps [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL data types to ODBC SQL data types.</span></span> <span data-ttu-id="a4fa2-104">次のセクションでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL データ型とマップ先の ODBC SQL データ型について説明します。</span><span class="sxs-lookup"><span data-stu-id="a4fa2-104">The sections below discuss the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL data types and the ODBC SQL data types to which they map.</span></span> <span data-ttu-id="a4fa2-105">また、ODBC SQL データ型と対応する ODBC C データ型、およびサポートされる変換と既定の変換についても説明します。</span><span class="sxs-lookup"><span data-stu-id="a4fa2-105">They also discuss the ODBC SQL data types and their corresponding ODBC C data types, and the supported and default conversions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a4fa2-106">Timestamp [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列の値は**datetime**値ではなく、行のアクティビティのシーケンスを**timestamp**示す**BINARY (8)** または**VARBINARY (8)** 値であるため、 **timestamp**データ型は SQL_BINARY または SQL_VARBINARY ODBC データ型にマップされます [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a4fa2-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**timestamp** data type maps to the SQL_BINARY or SQL_VARBINARY ODBC data type because the values in **timestamp** columns are not **datetime** values, but **binary(8)** or **varbinary(8)** values that indicate the sequence of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] activity on the row.</span></span> <span data-ttu-id="a4fa2-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、奇数バイトの SQL_C_WCHAR (Unicode) 型の値を処理する場合、末尾の奇数バイトが切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="a4fa2-107">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver encounters a SQL_C_WCHAR (Unicode) value that is an odd number of bytes, the trailing odd byte is truncated.</span></span>  
  
## <a name="dealing-with-sql_variant-data-type-in-odbc"></a><span data-ttu-id="a4fa2-108">ODBC での sql_variant データ型の処理</span><span class="sxs-lookup"><span data-stu-id="a4fa2-108">Dealing with sql_variant Data Type in ODBC</span></span>  
 <span data-ttu-id="a4fa2-109">**Sql_variant**データ型の列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **text**、 **ntext**、 **image**などのラージオブジェクト (lob) を除く、の任意のデータ型を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a4fa2-109">The **sql_variant** data type column can contain any of the data types in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] except large objects (LOBs), such as **text**, **ntext**, and **image**.</span></span> <span data-ttu-id="a4fa2-110">たとえば、列には、一部の行に対して**smallint**値、他の行の場合は**float**値、残りの場合は**char/nchar**値を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a4fa2-110">For example, the column could contain **smallint** values for some rows, **float** values for other rows, and **char/nchar** values in the remainder.</span></span>  
  
 <span data-ttu-id="a4fa2-111">**Sql_variant**のデータ型は、Microsoft Visual Basic の**variant**データ型に似てい??.</span><span class="sxs-lookup"><span data-stu-id="a4fa2-111">The **sql_variant** data type is similar to the **Variant** data type in Microsoft Visual Basic??.</span></span>  
  
### <a name="retrieving-data-from-the-server"></a><span data-ttu-id="a4fa2-112">サーバーからのデータの取得</span><span class="sxs-lookup"><span data-stu-id="a4fa2-112">Retrieving Data from the Server</span></span>  
 <span data-ttu-id="a4fa2-113">ODBC には、バリアント型の概念がないため、 **sql_variant**データ型の使用をの odbc ドライバーで制限し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="a4fa2-113">ODBC does not have a concept of variant types, limiting the use of the **sql_variant** data type with an ODBC driver in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a4fa2-114">では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バインドを指定する場合、 **sql_variant**のデータ型は、ドキュメント化されているいずれかの ODBC データ型にバインドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4fa2-114">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], if binding is specified, the **sql_variant** data type must be bound to one of the documented ODBC data types.</span></span> <span data-ttu-id="a4fa2-115">**SQL_CA_SS_VARIANT_TYPE**は、NATIVE Client ODBC ドライバーに固有の新しい属性で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 **sql_variant**列にあるインスタンスのデータ型をユーザーに返します。</span><span class="sxs-lookup"><span data-stu-id="a4fa2-115">**SQL_CA_SS_VARIANT_TYPE**, a new attribute specific to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver, returns the data type of an instance in the **sql_variant** column to the user.</span></span>  
  
 <span data-ttu-id="a4fa2-116">バインドが指定されていない場合は、 [SQLGetData](../native-client-odbc-api/sqlgetdata.md)関数を使用して、 **sql_variant**列のインスタンスのデータ型を特定できます。</span><span class="sxs-lookup"><span data-stu-id="a4fa2-116">If no binding is specified, the [SQLGetData](../native-client-odbc-api/sqlgetdata.md) function can be used to determine the data type of an instance in the **sql_variant** column.</span></span>  
  
 <span data-ttu-id="a4fa2-117">**Sql_variant**データを取得するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="a4fa2-117">To retrieve **sql_variant** data follow these steps.</span></span>  
  
1.  <span data-ttu-id="a4fa2-118">**Sqlfetch**を呼び出して、取得した行に移動します。</span><span class="sxs-lookup"><span data-stu-id="a4fa2-118">Call **SQLFetch** to position to the row retrieved.</span></span>  
  
2.  <span data-ttu-id="a4fa2-119">型に SQL_C_BINARY を指定し、データ長に0を指定して、 **SQLGetData**を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a4fa2-119">Call **SQLGetData**, specifying SQL_C_BINARY for the type and 0 for the data length.</span></span> <span data-ttu-id="a4fa2-120">これにより、ドライバーは**sql_variant**ヘッダーを強制的に読み取ります。</span><span class="sxs-lookup"><span data-stu-id="a4fa2-120">This forces the driver to read the **sql_variant** header.</span></span> <span data-ttu-id="a4fa2-121">ヘッダーは、そのインスタンスのデータ型を**sql_variant**列に提供します。</span><span class="sxs-lookup"><span data-stu-id="a4fa2-121">The header provides the data type of that instance in the **sql_variant** column.</span></span> <span data-ttu-id="a4fa2-122">**SQLGetData**は、値のサイズ (バイト単位) を返します。</span><span class="sxs-lookup"><span data-stu-id="a4fa2-122">**SQLGetData** returns the size (in bytes) of the value.</span></span>  
  
3.  <span data-ttu-id="a4fa2-123">属性値として**SQL_CA_SS_VARIANT_TYPE**を指定して[sqlcolattribute](../native-client-odbc-api/sqlcolattribute.md)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a4fa2-123">Call [SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) by specifying **SQL_CA_SS_VARIANT_TYPE** as its attribute value.</span></span> <span data-ttu-id="a4fa2-124">この関数は、 **sql_variant**列にあるインスタンスの C データ型をクライアントに返します。</span><span class="sxs-lookup"><span data-stu-id="a4fa2-124">This function will return the C data type of the instance in the **sql_variant** column to the client.</span></span>  
  
 <span data-ttu-id="a4fa2-125">上記の手順を行うコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="a4fa2-125">Here is a code segment showing the preceding steps.</span></span>  
  
```  
while ((retcode = SQLFetch (hstmt))==SQL_SUCCESS)  
{  
    if (retcode != SQL_SUCCESS && retcode != SQL_SUCCESS_WITH_INFO)  
    {  
        SQLError (NULL, NULL, hstmt, NULL,   
                    &lNativeError,szError,MAX_DATA,&sReturned);  
        printf_s ("%s\n",szError);  
        goto Exit;  
    }  
    retcode = SQLGetData (hstmt, 1, SQL_C_BINARY,   
                                pBuff,0,&Indicator);//Figure out the length  
    if (retcode != SQL_SUCCESS_WITH_INFO && retcode != SQL_SUCCESS)  
    {  
        SQLError (NULL, NULL, hstmt, NULL, &lNativeError,   
                    szError,MAX_DATA,&sReturned);  
        printf_s ("%s\n",szError);  
        goto Exit;  
    }  
    printf_s ("Byte length : %d ",Indicator); //Print out the byte length  
  
    int iValue = 0;  
    retcode = SQLColAttribute (hstmt, 1, SQL_CA_SS_VARIANT_TYPE, NULL,   
                                        NULL,NULL,&iValue);  //Figure out the type  
    printf_s ("Sub type = %d ",iValue);//Print the type, the return is C_type of the column]  
  
// Set up a new binding or do the SQLGetData on that column with   
// the appropriate type  
}  
```  
  
 <span data-ttu-id="a4fa2-126">ユーザーが[SQLBindCol](../native-client-odbc-api/sqlbindcol.md)を使用してバインドを作成すると、ドライバーはメタデータとデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="a4fa2-126">If the user creates the binding using [SQLBindCol](../native-client-odbc-api/sqlbindcol.md), the driver reads the metadata and the data.</span></span> <span data-ttu-id="a4fa2-127">次に、そのデータをバインドに指定されている適切な ODBC 型に変換します。</span><span class="sxs-lookup"><span data-stu-id="a4fa2-127">The driver then converts the data to the appropriate ODBC type specified in the binding.</span></span>  
  
### <a name="sending-data-to-the-server"></a><span data-ttu-id="a4fa2-128">サーバーへのデータの送信</span><span class="sxs-lookup"><span data-stu-id="a4fa2-128">Sending Data to the Server</span></span>  
 <span data-ttu-id="a4fa2-129">**SQL_SS_VARIANT**は、NATIVE Client ODBC ドライバーに固有の新しいデータ型で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **sql_variant**列に送信されるデータに使用されます。</span><span class="sxs-lookup"><span data-stu-id="a4fa2-129">**SQL_SS_VARIANT**, a new data type specific to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver, is used for data sent to an **sql_variant** column.</span></span> <span data-ttu-id="a4fa2-130">パラメーターを使用してサーバーにデータを送信する場合 (たとえば、INSERT INTO TableName VALUES (?,?))、 [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md)を使用して、C 型や対応する型などのパラメーター情報を指定し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="a4fa2-130">When sending data to the server using parameters (for example, INSERT INTO TableName VALUES (?,?)), [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) is used to specify the parameter information including the C type and the corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type.</span></span> <span data-ttu-id="a4fa2-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーは、C データ型を適切な**sql_variant**のサブタイプのいずれかに変換します。</span><span class="sxs-lookup"><span data-stu-id="a4fa2-131">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver will convert the C data type to one of the appropriate **sql_variant** subtypes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4fa2-132">参照</span><span class="sxs-lookup"><span data-stu-id="a4fa2-132">See Also</span></span>  
 [<span data-ttu-id="a4fa2-133">ODBC&#41;&#40;結果の処理</span><span class="sxs-lookup"><span data-stu-id="a4fa2-133">Processing Results &#40;ODBC&#41;</span></span>](processing-results-odbc.md)  
  
  

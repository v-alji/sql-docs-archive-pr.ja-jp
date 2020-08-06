---
title: 結果セットの特性の決定 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], characteristics
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- SQLDescribeCol function
- metadata [ODBC]
- SQLColAttribute function
- SQLNumResultCols function
ms.assetid: 90be414c-04b3-46c0-906b-ae7537989b7d
author: rothja
ms.author: jroth
ms.openlocfilehash: 5957092cdddfbcbce904d9a6483914672565d337
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634499"
---
# <a name="determining-the-characteristics-of-a-result-set-odbc"></a><span data-ttu-id="ad3f6-102">結果セットの特性の決定 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="ad3f6-102">Determining the Characteristics of a Result Set (ODBC)</span></span>
  <span data-ttu-id="ad3f6-103">メタデータは、他のデータを説明するデータです。</span><span class="sxs-lookup"><span data-stu-id="ad3f6-103">Metadata is data that describes other data.</span></span> <span data-ttu-id="ad3f6-104">たとえば、結果セットのメタデータは、結果セットに含まれる列数、これらの列のデータ型、名前、有効桁数、NULL 値の許容属性など、結果セットの特性を説明します。</span><span class="sxs-lookup"><span data-stu-id="ad3f6-104">For example, result set metadata describes the characteristics of a result set, such as the number of columns in the result set, the data types of those columns, their names, precision, and nullability.</span></span>  
  
 <span data-ttu-id="ad3f6-105">ODBC は、ODBC のカタログ API 関数を使用してアプリケーションにメタデータを渡します。</span><span class="sxs-lookup"><span data-stu-id="ad3f6-105">ODBC supplies metadata to applications through its catalog API functions.</span></span> <span data-ttu-id="ad3f6-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT odbc ドライバーでは、対応するカタログプロシージャへの呼び出しとして、多くの ODBC API カタログ関数が実装されて [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] います。</span><span class="sxs-lookup"><span data-stu-id="ad3f6-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver implements many of the ODBC API catalog functions as calls to a corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] catalog procedure.</span></span>  
  
 <span data-ttu-id="ad3f6-107">アプリケーションは、ほとんどの結果セット操作にメタデータを必要とします。</span><span class="sxs-lookup"><span data-stu-id="ad3f6-107">Applications require metadata for most result set operations.</span></span> <span data-ttu-id="ad3f6-108">たとえば、列のデータ型を使用して、列にバインドされている変数の種類を判断します。</span><span class="sxs-lookup"><span data-stu-id="ad3f6-108">For example, the application uses the data type of a column to determine what kind of variable to bind to that column.</span></span> <span data-ttu-id="ad3f6-109">または、文字型の列のバイト長を使用して、その列のデータの表示に必要な領域サイズを判断します。</span><span class="sxs-lookup"><span data-stu-id="ad3f6-109">It uses the byte length of a character column to determine how much space it must have to display data from that column.</span></span> <span data-ttu-id="ad3f6-110">アプリケーションが列のメタデータを判断する方法は、アプリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="ad3f6-110">How an application determines the metadata for a column depends on the type of the application.</span></span>  
  
 <span data-ttu-id="ad3f6-111">業種特有のアプリケーションでは、通常、事前定義されたテーブルを使用して、これらのテーブルに対して事前に定義された操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="ad3f6-111">Vertical applications typically work with predefined tables and perform predefined operations on those tables.</span></span> <span data-ttu-id="ad3f6-112">このようなアプリケーション用の結果セットのメタデータは、アプリケーションが作成される前に既に定義され、開発者が制御するので、アプリケーションにハードコーディングできます。</span><span class="sxs-lookup"><span data-stu-id="ad3f6-112">Because the result set metadata for such applications is defined before the application is even written and is controlled by the developer, it can be hard-coded into the application.</span></span> <span data-ttu-id="ad3f6-113">たとえば、データ ソース内で受注 ID 列が 4 バイト integer 型で定義されている場合、アプリケーションは常に 4 バイト integer をこの列にバインドできます。</span><span class="sxs-lookup"><span data-stu-id="ad3f6-113">For example, if an order ID column is defined as a 4-byte integer in the data source, the application can always bind a 4-byte integer to that column.</span></span> <span data-ttu-id="ad3f6-114">メタデータがアプリケーション内でハードコーディングされている場合、アプリケーションが使用するテーブルへの変更は、通常、アプリケーション コードに対する変更になります。</span><span class="sxs-lookup"><span data-stu-id="ad3f6-114">When metadata is hard-coded in the application, a change to the tables used by the application generally implies a change to the application code.</span></span>  
  
 <span data-ttu-id="ad3f6-115">汎用アプリケーション、特にアドホック クエリをサポートするアプリケーションでは、アプリケーションが作成する結果セットのメタデータは、通常実行時まで特定できません。</span><span class="sxs-lookup"><span data-stu-id="ad3f6-115">In generic applications, especially applications that support ad hoc queries, the metadata of the result sets they create is typically unknown until run time.</span></span>  
  
 <span data-ttu-id="ad3f6-116">アプリケーションは次の関数を呼び出すことで、結果セットの特性を判断できます。</span><span class="sxs-lookup"><span data-stu-id="ad3f6-116">To determine the characteristics of a result set, an application can call:</span></span>  
  
-   <span data-ttu-id="ad3f6-117">要求から返される列の数を確認するには、 [Sqlnumresultcols](../native-client-odbc-api/sqlnumresultcols.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="ad3f6-117">[SQLNumResultCols](../native-client-odbc-api/sqlnumresultcols.md) to determine how many columns a request returned.</span></span>  
  
-   <span data-ttu-id="ad3f6-118">[Sqlcolattribute](../native-client-odbc-api/sqlcolattribute.md)または[SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md)を実行して、結果セット内の列を記述します。</span><span class="sxs-lookup"><span data-stu-id="ad3f6-118">[SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) or [SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md) to describe a column in the result set.</span></span>  
  
 <span data-ttu-id="ad3f6-119">適切にデザインされたアプリケーションを作成する場合、結果セットの状態が不明であることが前提となります。またアプリケーションでは、これらの関数により返される情報を使用して結果セットの列をバインドします。</span><span class="sxs-lookup"><span data-stu-id="ad3f6-119">A well-designed application is written with the assumption that the result set is unknown and uses the information returned by these functions to bind the columns in the result set.</span></span> <span data-ttu-id="ad3f6-120">アプリケーションは、ステートメントが準備または実行されると、いつでもこれらの関数を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="ad3f6-120">An application can call these functions at any time after a statement is prepared or executed.</span></span> <span data-ttu-id="ad3f6-121">ただし、最適なパフォーマンスを得るには、ステートメントの実行後に、アプリケーションで**Sqlcolattribute**、 **SQLDescribeCol**、および**sqlnumresultcols**を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad3f6-121">However, for optimal performance, an application should call **SQLColAttribute**, **SQLDescribeCol**, and **SQLNumResultCols** after a statement is executed.</span></span>  
  
 <span data-ttu-id="ad3f6-122">メタデータを取得するための呼び出しを複数同時に実行できます。</span><span class="sxs-lookup"><span data-stu-id="ad3f6-122">You can have multiple concurrent calls for metadata.</span></span> <span data-ttu-id="ad3f6-123">ODBC カタログ API 実装の基盤であるシステム カタログ プロシージャは、ODBC ドライバーが静的サーバー カーソルを使用しているときでも ODBC ドライバーから呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="ad3f6-123">The system catalog procedures underlying the ODBC catalog API implementations can be called by the ODBC driver while it is using static server cursors.</span></span> <span data-ttu-id="ad3f6-124">このため、アプリケーションは ODBC カタログ関数の複数の呼び出しを同時に処理できます。</span><span class="sxs-lookup"><span data-stu-id="ad3f6-124">This lets applications concurrently process multiple calls to ODBC catalog functions.</span></span>  
  
 <span data-ttu-id="ad3f6-125">アプリケーションが特定のメタデータのセットを複数回使用する場合、関数からの情報を最初に取得した時点でプライベート変数に格納すると、メタデータの利点を活用することができます。</span><span class="sxs-lookup"><span data-stu-id="ad3f6-125">If an application uses a particular set of metadata more than one time, it will probably benefit from caching the information in private variables when it is first obtained.</span></span> <span data-ttu-id="ad3f6-126">このような操作を行うと、同じ情報を取得するために、ドライバーとサーバー間のラウンドトリップが必要になる ODBC カタログ関数の呼び出しを後で実行する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="ad3f6-126">This prevents later calls to the ODBC catalog functions for the same information, which force the driver to make round trips to the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad3f6-127">参照</span><span class="sxs-lookup"><span data-stu-id="ad3f6-127">See Also</span></span>  
 [<span data-ttu-id="ad3f6-128">ODBC&#41;&#40;結果の処理</span><span class="sxs-lookup"><span data-stu-id="ad3f6-128">Processing Results &#40;ODBC&#41;</span></span>](processing-results-odbc.md)  
  
  

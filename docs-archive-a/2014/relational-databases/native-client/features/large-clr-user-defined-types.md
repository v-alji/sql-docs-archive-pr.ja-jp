---
title: 大きな CLR ユーザー定義型 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- large CLR user-defined types
ms.assetid: b65eb61d-ccf6-49c0-98e7-9a4ef4b2f790
author: rothja
ms.author: jroth
ms.openlocfilehash: 27f0c13caea8c4aca63d78238509c6d05f1bf7bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714274"
---
# <a name="large-clr-user-defined-types"></a><span data-ttu-id="f44d4-102">大きな CLR ユーザー定義型</span><span class="sxs-lookup"><span data-stu-id="f44d4-102">Large CLR User-Defined Types</span></span>
  <span data-ttu-id="f44d4-103">SQL Server 2005 では、共通言語ランタイム (CLR) のユーザー定義型 (UDT) のサイズは 8,000 バイトに制限されていました。</span><span class="sxs-lookup"><span data-stu-id="f44d4-103">In SQL Server 2005, user-defined types (UDTs) in the common language runtime (CLR) were restricted to 8,000 bytes in size.</span></span> <span data-ttu-id="f44d4-104">[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 以降では、この制限が解除されます。</span><span class="sxs-lookup"><span data-stu-id="f44d4-104">This restriction has been lifted in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] and later versions.</span></span> <span data-ttu-id="f44d4-105">CLR UDT はラージ オブジェクト (LOB) 型と同様に扱われるようになりました。</span><span class="sxs-lookup"><span data-stu-id="f44d4-105">CLR UDTs are now treated in a similar way to large object (LOB) types.</span></span> <span data-ttu-id="f44d4-106">つまり、8,000 バイト以下の UDT は SQL Server 2005 の場合と同じように動作しますが、8,000 バイトを超える UDT もサポートされるようになり、そのサイズは "無制限" として報告されます。</span><span class="sxs-lookup"><span data-stu-id="f44d4-106">That is, UDTs less than or equal to 8,000 bytes behave the same way as in SQL Server 2005, but larger UDTs are supported and report their size as "unlimited".</span></span>  
  
 <span data-ttu-id="f44d4-107">詳細については、「 [&#40;&#41;OLE DB の大きな Clr ユーザー定義型](../ole-db/large-clr-user-defined-types-ole-db.md)」を参照してください。また、 [&#40;ODBC&#41;の大きな Clr ユーザー定義型](../odbc/large-clr-user-defined-types-odbc.md)については、「」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f44d4-107">For more information, see [Large CLR User-Defined Types &#40;OLE DB&#41;](../ole-db/large-clr-user-defined-types-ole-db.md) and [Large CLR User-Defined Types &#40;ODBC&#41;](../odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="use-cases"></a><span data-ttu-id="f44d4-108">例</span><span class="sxs-lookup"><span data-stu-id="f44d4-108">Use Cases</span></span>  
 <span data-ttu-id="f44d4-109">ODBC の場合、大きな UDT のサポートには、UDT 値を実行時データ パラメーターとして個別に送信する機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f44d4-109">For ODBC, support for large UDTs includes the ability to send UDT values in pieces as data-at-execution parameters.</span></span> <span data-ttu-id="f44d4-110">これを行うには、SQLPutData を使用します。</span><span class="sxs-lookup"><span data-stu-id="f44d4-110">This is done by using SQLPutData.</span></span>  
  
 <span data-ttu-id="f44d4-111">OLE DB の場合、大きな UDT のサポートには、ISequentialStream バインドを使用したサーバーとの間の UDT 値のストリームの送受信機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f44d4-111">For OLE DB, support for large UDTs includes the ability to stream UDT values to and from the server by using ISequentialStream binding.</span></span>  
  
 <span data-ttu-id="f44d4-112">8,000 バイト以下の UDT は SQL Server 2005 の場合と同じように動作します。</span><span class="sxs-lookup"><span data-stu-id="f44d4-112">UDTs less than or equal to 8,000 bytes will behave as they did in SQL Server 2005.</span></span> <span data-ttu-id="f44d4-113">OLE DB では、ISequentialStream バインドを使用して、小さな UDT をストリーム処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="f44d4-113">For OLE DB, you can still stream small UDTs by using ISequentialStream binding.</span></span>  
  
 <span data-ttu-id="f44d4-114">場合によっては、ネイティブ コードで CLR UDT のコンテンツを認識する必要がありますが、マネージド オブジェクトのインスタンスを作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f44d4-114">Sometimes native code will have to understand the contents of CLR UDTs, but will not have to instantiate managed objects.</span></span> <span data-ttu-id="f44d4-115">この場合は、カスタムのシリアル化を使用して、サーバーの UDT 値をクライアントで認識される形式に変換することができます。</span><span class="sxs-lookup"><span data-stu-id="f44d4-115">If this is the case, you can use custom serialization to convert UDT values on the server into a well known format for clients.</span></span>  
  
 <span data-ttu-id="f44d4-116">既存のデータ アクセス コードを使用するアプリケーションの場合は、クライアント側で CLR UDT の動作を利用できます。そのためには、ネイティブ API を使用して UDT を取得し、混合モードのアプリケーションで C++ CLI 相互運用機能を使用して UDT のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="f44d4-116">For applications that have existing data access code, you can exploit CLR UDT behavior on the client by retrieving UDTs through native APIs and instantiating them by using C++ CLI interop in mixed mode applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f44d4-117">参照</span><span class="sxs-lookup"><span data-stu-id="f44d4-117">See Also</span></span>  
 [<span data-ttu-id="f44d4-118">SQL Server Native Client の機能</span><span class="sxs-lookup"><span data-stu-id="f44d4-118">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  

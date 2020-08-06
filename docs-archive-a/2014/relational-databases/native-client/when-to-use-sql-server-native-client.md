---
title: SQL Server Native Client を使用する場合 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- SQLNCLI, about SQL Server Native Client
- data access [SQL Server Native Client], about SQL Server Native Client
ms.assetid: 08f18b36-209d-4cf7-9623-ebc61859a91d
author: rothja
ms.author: jroth
ms.openlocfilehash: f8aeb34525bbe5c1b003e8fd95e7a414025965a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639471"
---
# <a name="when-to-use-sql-server-native-client"></a><span data-ttu-id="c652d-102">SQL Server Native Client を使用する場合</span><span class="sxs-lookup"><span data-stu-id="c652d-102">When to Use SQL Server Native Client</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c652d-103">Native Client は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのデータにアクセスする際に使用できるテクノロジの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="c652d-103">Native Client is one technology that you can use to access data in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  <span data-ttu-id="c652d-104">各種データ アクセス テクノロジの詳細については、「[データ アクセス テクノロジのロードマップ](https://go.microsoft.com/fwlink/?LinkID=179186)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c652d-104">For a discussion of the different data-access technologies, see [Data Access Technologies Road Map](https://go.microsoft.com/fwlink/?LinkID=179186)</span></span>  
  
 <span data-ttu-id="c652d-105">アプリケーションのデータ アクセス テクノロジとして [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client を使用するかどうかを決める場合は、いくつかの要素を検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c652d-105">When deciding whether to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client as the data access technology of your application, you should consider several factors.</span></span>  
  
 <span data-ttu-id="c652d-106">新しいアプリケーションで、Microsoft Visual C# や Visual Basic などのマネージド プログラミング言語を使用しており、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新機能にアクセスする必要がある場合は、.NET Framework に含まれている .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c652d-106">For new applications, if you're using a managed programming language such as Microsoft Visual C# or Visual Basic, and you need to access the new features in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you should use the .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], which is part of the .NET Framework.</span></span>  
  
 <span data-ttu-id="c652d-107">COM ベースのアプリケーションを開発しており、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で導入された新機能にアクセスする必要がある場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c652d-107">If you are developing a COM-based application and need to access the new features introduced in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you should use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="c652d-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新機能にアクセスする必要がない場合は、引き続き Windows Data Access Components (WDAC) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c652d-108">If you don't need access to the new features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can continue to use Windows Data Access Components (WDAC).</span></span>  
  
 <span data-ttu-id="c652d-109">既存の OLE DB アプリケーションや ODBC アプリケーションの場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新機能にアクセスする必要があるかどうかが重要な問題になります。</span><span class="sxs-lookup"><span data-stu-id="c652d-109">For existing OLE DB and ODBC applications, the primary issue is whether you need to access the new features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c652d-110">アプリケーションが既に完成していて、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新機能を必要としない場合は、引き続き WDAC を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c652d-110">If you have a mature application that does not need the new features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can continue to use WDAC.</span></span> <span data-ttu-id="c652d-111">ただし、 [xml データ型](/sql/t-sql/xml/xml-transact-sql)などの新機能にアクセスする必要がある場合は、Native Client を使用する必要があり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="c652d-111">But if you do need to access those new features, such as the [xml data type](/sql/t-sql/xml/xml-transact-sql), you should use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 <span data-ttu-id="c652d-112">行のバージョン管理機能を使用した Read Committed トランザクション分離は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client と MDAC の両方でサポートされていますが、スナップショット トランザクション分離は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client のみでサポートされています </span><span class="sxs-lookup"><span data-stu-id="c652d-112">Both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client and MDAC support read committed transaction isolation using row versioning, but only [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client supports snapshot transaction isolation.</span></span> <span data-ttu-id="c652d-113">(プログラミング用語では、"行のバージョン管理機能を使用した Read Committed トランザクション分離" は "Read Committed トランザクション" と同義です)。</span><span class="sxs-lookup"><span data-stu-id="c652d-113">(In programming terms, read committed transaction isolation with row versioning is the same as Read-Committed transaction.)</span></span>  
  
 <span data-ttu-id="c652d-114">Native Client と MDAC の違いについては [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「 [mdac から SQL Server Native Client するようにアプリケーションを更新する](../../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c652d-114">For information about the differences between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client and MDAC, see [Updating an Application to SQL Server Native Client from MDAC](../../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c652d-115">参照</span><span class="sxs-lookup"><span data-stu-id="c652d-115">See Also</span></span>  
 <span data-ttu-id="c652d-116">[SQL Server Native Client プログラミング](../../relational-databases/native-client/sql-server-native-client-programming.md) </span><span class="sxs-lookup"><span data-stu-id="c652d-116">[SQL Server Native Client Programming](../../relational-databases/native-client/sql-server-native-client-programming.md) </span></span>  
 <span data-ttu-id="c652d-117">[ODBC の操作方法に関するトピック](../native-client-odbc-how-to/odbc-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="c652d-117">[ODBC How-to Topics](../native-client-odbc-how-to/odbc-how-to-topics.md) </span></span>  
 [<span data-ttu-id="c652d-118">OLE DB の使用法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="c652d-118">OLE DB How-to Topics</span></span>](../native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  

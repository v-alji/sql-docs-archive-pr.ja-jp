---
title: SQLXML が SQL Server | にインストールされていません。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 3dbb4f65-41de-48b8-ad62-47c9d7932de3
author: rothja
ms.author: jroth
ms.openlocfilehash: ffa4cfd8b18dbfd9b4ba05599e2a973ac5f6e888
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642666"
---
# <a name="sqlxml-is-not-installed-in-sql-server"></a><span data-ttu-id="24c29-102">SQL Server で SQLXML がインストールされない</span><span class="sxs-lookup"><span data-stu-id="24c29-102">SQLXML Is Not Installed in SQL Server</span></span>
  <span data-ttu-id="24c29-103">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] より前のバージョンでは、SQLXML 4.0 は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に付属してリリースされ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのバージョン ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] を除く) の既定のインストールに含まれていました。</span><span class="sxs-lookup"><span data-stu-id="24c29-103">Before [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], SQLXML 4.0 was released with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and was part of the default installation of all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions except for [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span> <span data-ttu-id="24c29-104">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には、SQLXML の最新バージョン (SQLXML 4.0 SP1) が含まれないようになりました。</span><span class="sxs-lookup"><span data-stu-id="24c29-104">Starting with [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the latest version of SQLXML (SQLXML 4.0 SP1) is no longer included in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="24c29-105">SQLXML 4.0 SP1 が使用可能な場合にインストールするには、 [SQLXML sp1 のインストール場所](https://www.microsoft.com/download/details.aspx?id=44272)からダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="24c29-105">To install SQLXML 4.0 SP1 when it is available, download it from [Install Location for SQLXML SP1](https://www.microsoft.com/download/details.aspx?id=44272).</span></span>  
  
 <span data-ttu-id="24c29-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で実行されるアプリケーションに SQLXML 4.0 が必要な場合、およびコンピューターに [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] がインストールされていない場合は、SQLXML 4.0 SP1 をダウンロードしてインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="24c29-106">If an application runs on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and requires SQLXML 4.0, and if the computer does not have [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], you must download and install SQLXML 4.0 SP1.</span></span>  
  
## <a name="sqlxml-40-sp1-behavior-with-new-data-types-using-sqloledb-and-sql-server-native-client-ole-db-provider"></a><span data-ttu-id="24c29-107">SQLOLEDB および SQL Server Native Client OLE DB プロバイダーを使用した場合の新しいデータ型による SQLXML 4.0 SP1 の動作</span><span class="sxs-lookup"><span data-stu-id="24c29-107">SQLXML 4.0 SP1 Behavior with New Data Types Using SQLOLEDB and SQL Server Native Client OLE DB Provider</span></span>  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] <span data-ttu-id="24c29-108">では、SQLXML を利用する開発者が使用できる、次のデータ型が導入されています。</span><span class="sxs-lookup"><span data-stu-id="24c29-108">introduces the following data types, which developers using SQLXML might want to use:</span></span>  
  
-   `Date`  
  
-   `Time`  
  
-   `DateTime2`  
  
-   `DateTimeOffset`  
  
 <span data-ttu-id="24c29-109">(Windows Data Access Components、以前の Microsoft Data Access Components の) SQLOLEDB または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以降の [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Native Client OLE DB と共に SQLXML 4.0 SP1 を使用する場合、これらの新しいデータ型は文字列として表示されます。</span><span class="sxs-lookup"><span data-stu-id="24c29-109">When using SQLXML 4.0 SP1 with either SQLOLEDB (from Windows Data Access Components, formerly Microsoft Data Access Components) or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], these new types will appear as strings to a developer.</span></span> <span data-ttu-id="24c29-110">SQLXML 4.0 SP1 を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider 11.0 と共に使用した場合、この 4 つの新しいデータ型は組み込みスカラー型として有効になります。</span><span class="sxs-lookup"><span data-stu-id="24c29-110">SQLXML 4.0 SP1 will enable these four new data types as built-in scalar types when used with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider 11.0.</span></span> <span data-ttu-id="24c29-111">SQLXML 4.0 SP1 をダウンロードしないと、これらの型を文字列以外の型にマッピングした場合、一部のデータが切り捨てられる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="24c29-111">Until you download SQLXML 4.0 SP1, mapping these types to non-string types might cause truncation of some data.</span></span> <span data-ttu-id="24c29-112">たとえば、にマッピング `DateTime2` すると、 `xsd:date` データが [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] `DateTime` 3.33 ミリ秒の有効桁数に切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="24c29-112">For example, mapping `DateTime2` to `xsd:date` will cause data to be truncated to the [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] `DateTime` precision of 3.33 milliseconds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24c29-113">参照</span><span class="sxs-lookup"><span data-stu-id="24c29-113">See Also</span></span>  
 [<span data-ttu-id="24c29-114">SQLXML 4.0 のプログラミング概念</span><span class="sxs-lookup"><span data-stu-id="24c29-114">SQLXML 4.0 Programming Concepts</span></span>](sqlxml-4-0-programming-concepts.md)  
  
  

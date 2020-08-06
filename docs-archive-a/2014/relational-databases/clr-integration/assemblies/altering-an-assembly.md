---
title: アセンブリを変更する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration], modifying
- permissions [CLR integration]
- altering assemblies
- ALTER ASSEMBLY statement
ms.assetid: 9e765fbd-f339-473c-8537-22f478e79696
author: rothja
ms.author: jroth
ms.openlocfilehash: c22ca979675d3b7f263e3bc6de0c41c134a1abcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720048"
---
# <a name="altering-an-assembly"></a><span data-ttu-id="a774d-102">アセンブリの変更</span><span class="sxs-lookup"><span data-stu-id="a774d-102">Altering an Assembly</span></span>
  <span data-ttu-id="a774d-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に登録されているアセンブリは、ALTER ASSEMBLY ステートメントを使用することで、比較的最近のバージョンから更新できます。</span><span class="sxs-lookup"><span data-stu-id="a774d-103">Assemblies that have been registered in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] can be updated from a more recent version using the ALTER ASSEMBLY statement.</span></span> <span data-ttu-id="a774d-104">アセンブリを更新するには、ALTER ASSEMBLY ステートメントを次の構文で使用します。</span><span class="sxs-lookup"><span data-stu-id="a774d-104">To update an assembly, use the ALTER ASSEMBLY statement with the following syntax:</span></span>  
  
```  
ALTER ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
```  
  
 <span data-ttu-id="a774d-105">ALTER ASSEMBLY を使用しても、そのアセンブリを使用している現在実行中のプロセスは中断されません。プロセスの実行は、変更されていないアセンブリを使用して継続されます。</span><span class="sxs-lookup"><span data-stu-id="a774d-105">ALTER ASSEMBLY does not disrupt currently running processes that are using the assembly; the processes continue executing with the unaltered assembly.</span></span> <span data-ttu-id="a774d-106">ALTER ASSEMBLY を使用して、共通言語ランタイム (CLR) 関数、集計関数、ストアド プロシージャ、およびトリガーの署名を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="a774d-106">ALTER ASSEMBLY cannot be used to change the signatures of common language runtime (CLR) functions, aggregate functions, stored procedures, and triggers.</span></span> <span data-ttu-id="a774d-107">アセンブリに新しいパブリック メソッドを追加したり、プライベート メソッドを任意の方法で変更したりできます。パブリック メソッドは、署名または属性を変更しない限り変更できます。</span><span class="sxs-lookup"><span data-stu-id="a774d-107">New public methods can be added to the assembly, private methods can be modified in any way, and public methods can be modified as long as signatures or attributes are not changed.</span></span> <span data-ttu-id="a774d-108">データ メンバーや基本クラスなどの、ネイティブ シリアル化されたユーザー定義型に含まれているフィールドは、ALTER ASSEMBLY を使用して変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="a774d-108">Fields that are contained within a native-serialized user-defined type, including data members or base classes, cannot be changed by using ALTER ASSEMBLY.</span></span> <span data-ttu-id="a774d-109">その他の変更はいずれもサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a774d-109">All other changes are unsupported.</span></span> <span data-ttu-id="a774d-110">詳細については、「 [ALTER ASSEMBLY &#40;transact-sql&#41;](/sql/t-sql/statements/alter-assembly-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a774d-110">For more information, see [ALTER ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-assembly-transact-sql).</span></span>  
  
## <a name="changing-the-permission-set-of-an-assembly"></a><span data-ttu-id="a774d-111">アセンブリの権限セットの変更</span><span class="sxs-lookup"><span data-stu-id="a774d-111">Changing the Permission Set of an Assembly</span></span>  
 <span data-ttu-id="a774d-112">アセンブリの権限セットも、ALTER ASSEMBLY ステートメントを使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="a774d-112">The permission set of an assembly can also be changed using the ALTER ASSEMBLY statement.</span></span> <span data-ttu-id="a774d-113">次に示すステートメントでは、SQLCLRTest アセンブリの権限セットを `EXTERNAL_ACCESS` に変更します。</span><span class="sxs-lookup"><span data-stu-id="a774d-113">The following statement changes the permission set of the SQLCLRTest assembly to `EXTERNAL_ACCESS`.</span></span>  
  
```  
ALTER ASSEMBLY SQLCLRTest  
WITH PERMISSION_SET = EXTERNAL_ACCESS   
```  
  
 <span data-ttu-id="a774d-114">アセンブリの権限セットを `SAFE` から `EXTERNAL_ACCESS` または `UNSAFE` に変更する場合は、非対称キーと、それに対応する、そのアセンブリの `EXTERNAL ACCESS ASSEMBLY` 権限または `UNSAFE ASSEMBLY` 権限を持つログインを先に作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="a774d-114">If the permission set of an assembly is being changed from `SAFE` to `EXTERNAL_ACCESS` or `UNSAFE`, an asymmetric key and corresponding login with `EXTERNAL ACCESS ASSEMBLY` permission or `UNSAFE ASSEMBLY` permission for the assembly must first be created.</span></span> <span data-ttu-id="a774d-115">詳細については、「 [アセンブリの作成](creating-an-assembly.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a774d-115">For more information, see [Creating an Assembly](creating-an-assembly.md).</span></span>  
  
## <a name="adding-the-source-code-of-an-assembly"></a><span data-ttu-id="a774d-116">アセンブリのソース コードの追加</span><span class="sxs-lookup"><span data-stu-id="a774d-116">Adding the Source Code of an Assembly</span></span>  
 <span data-ttu-id="a774d-117">ALTER ASSEMBLY 構文の ADD FILE 句は、CREATE ASSEMBLY 構文には存在しません。</span><span class="sxs-lookup"><span data-stu-id="a774d-117">The ADD FILE clause in the ALTER ASSEMBLY syntax is not present in CREATE ASSEMBLY.</span></span> <span data-ttu-id="a774d-118">ADD FILE 句を使用すると、アセンブリに関連付けられるソース コードやその他のファイルを追加できます。</span><span class="sxs-lookup"><span data-stu-id="a774d-118">You can use it to add source code or any other files associated with an assembly.</span></span> <span data-ttu-id="a774d-119">ファイルは元の場所からコピーされ、データベース内のシステム テーブルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="a774d-119">The files are copied from their original locations and stored in system tables in the database.</span></span> <span data-ttu-id="a774d-120">これにより、現在のバージョンの UDT を再作成またはドキュメント化する必要があれば、ソース コードや他のファイルをいつでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="a774d-120">This ensures that you always have source code or other files on hand should you ever need to re-create or document the current version of the UDT.</span></span>  
  
 <span data-ttu-id="a774d-121">次に示すステートメントでは、Point UDT の Point.cs クラスのソース コードを追加しています。</span><span class="sxs-lookup"><span data-stu-id="a774d-121">The following statement adds the Point.cs class source code for the Point UDT.</span></span> <span data-ttu-id="a774d-122">Point.cs ファイルに含まれているテキストがコピーされ、"PointSource" という名前でデータベースに格納されます。</span><span class="sxs-lookup"><span data-stu-id="a774d-122">This copies the text contained in the Point.cs file and stores it in the database under the name "PointSource".</span></span>  
  
 `ALTER ASSEMBLY Point`  
  
 `ADD FILE FROM 'C:\Projects\Point\Point.cs' AS PointSource`  
  
## <a name="see-also"></a><span data-ttu-id="a774d-123">参照</span><span class="sxs-lookup"><span data-stu-id="a774d-123">See Also</span></span>  
 <span data-ttu-id="a774d-124">[CLR 統合アセンブリの管理](managing-clr-integration-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="a774d-124">[Managing CLR Integration Assemblies](managing-clr-integration-assemblies.md) </span></span>  
 <span data-ttu-id="a774d-125">[アセンブリの作成](creating-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="a774d-125">[Creating an Assembly](creating-an-assembly.md) </span></span>  
 <span data-ttu-id="a774d-126">[アセンブリの削除](dropping-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="a774d-126">[Dropping an Assembly](dropping-an-assembly.md) </span></span>  
 [<span data-ttu-id="a774d-127">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a774d-127">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
  

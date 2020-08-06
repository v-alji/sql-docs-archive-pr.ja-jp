---
title: ネイティブ コンパイル ストアド プロシージャ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
helpviewer_keywords:
- natively compiled stored procedures
ms.assetid: d5ed432c-10c5-4e4f-883c-ef4d1fa32366
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b8fb7a379c0c08ca357baa1042ebcf51c512c9ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738377"
---
# <a name="natively-compiled-stored-procedures"></a><span data-ttu-id="1f019-102">ネイティブ コンパイル ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="1f019-102">Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="1f019-103">ネイティブ コンパイル ストアド プロシージャは、ネイティブ コードにコンパイルされる [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャであり、メモリ最適化テーブルにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="1f019-103">Natively compiled stored procedures are [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures compiled to native code that access memory-optimized tables.</span></span> <span data-ttu-id="1f019-104">ネイティブ コンパイル ストアド プロシージャにより、ストアド プロシージャ内でクエリやビジネス ロジックを効率的に実行できます。</span><span class="sxs-lookup"><span data-stu-id="1f019-104">Natively compiled stored procedures allow for efficient execution of queries and business logic in the stored procedure.</span></span> <span data-ttu-id="1f019-105">ネイティブ コンパイル処理の詳細については、「 [テーブルとストアド プロシージャのネイティブ コンパイル](native-compilation-of-tables-and-stored-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f019-105">For more details about the native compilation process, see [Native Compilation of Tables and Stored Procedures](native-compilation-of-tables-and-stored-procedures.md).</span></span> <span data-ttu-id="1f019-106">ディスク ベース ストアド プロシージャをネイティブ コンパイル ストアド プロシージャに移行する方法の詳細については、「 [ネイティブ コンパイル ストアド プロシージャの移行に関する問題](migration-issues-for-natively-compiled-stored-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f019-106">For more information about migrating disk-based stored procedures to natively compiled stored procedures, see [Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1f019-107">解釈された (ディスク ベースの) ストアド プロシージャとネイティブ コンパイル ストアド プロシージャの相違点の 1 つは、解釈されたストアド プロシージャは最初の実行時にコンパイルされ、ネイティブ コンパイル ストアド プロシージャは作成時にコンパイルされる点です。</span><span class="sxs-lookup"><span data-stu-id="1f019-107">One difference between interpreted (disk-based) stored procedures and natively compiled stored procedures is that an interpreted stored procedure is compiled at first execution whereas a natively compiled stored procedure is compiled when it is created.</span></span> <span data-ttu-id="1f019-108">ネイティブコンパイルストアドプロシージャでは、多くのエラー条件 (算術オーバーフロー、型変換、および0除算の条件) を作成時に検出でき、ネイティブコンパイルストアドプロシージャの作成が失敗します。</span><span class="sxs-lookup"><span data-stu-id="1f019-108">With natively compiled stored procedures, many error conditions (arithmetic overflow, type conversion, and some divide-by-zero conditions) can be detected at create time and will cause creation of the natively compiled stored procedure to fail.</span></span> <span data-ttu-id="1f019-109">解釈されたストアド プロシージャでは、通常、このようなエラー状態によってストアド プロシージャの作成時にエラーが発生することはありませんが、実行はすべて失敗します。</span><span class="sxs-lookup"><span data-stu-id="1f019-109">With interpreted stored procedures, these error conditions will typically not cause a failure when the stored procedure is created, but all executions will fail.</span></span>  
  
 <span data-ttu-id="1f019-110">このセクションのトピック:</span><span class="sxs-lookup"><span data-stu-id="1f019-110">Topics in this section:</span></span>  
  
-   [<span data-ttu-id="1f019-111">ネイティブ コンパイル ストアド プロシージャの作成</span><span class="sxs-lookup"><span data-stu-id="1f019-111">Creating Natively Compiled Stored Procedures</span></span>](creating-natively-compiled-stored-procedures.md)  
  
-   [<span data-ttu-id="1f019-112">Atomic ブロック</span><span class="sxs-lookup"><span data-stu-id="1f019-112">Atomic Blocks</span></span>](atomic-blocks-in-native-procedures.md)  
  
-   [<span data-ttu-id="1f019-113">ネイティブ コンパイル ストアド プロシージャ内でサポートされる構造</span><span class="sxs-lookup"><span data-stu-id="1f019-113">Supported Constructs in Natively Compiled Stored Procedures</span></span>](supported-features-for-natively-compiled-t-sql-modules.md)  
  
-   [<span data-ttu-id="1f019-114">ネイティブ コンパイル ストアド プロシージャでの Try..Catch の使用</span><span class="sxs-lookup"><span data-stu-id="1f019-114">Using Try..Catch in Natively Compiled Stored Procedures</span></span>](../../database-engine/using-try-catch-in-natively-compiled-stored-procedures.md)  
  
-   [<span data-ttu-id="1f019-115">ネイティブ コンパイル ストアド プロシージャ上でサポートされる構造</span><span class="sxs-lookup"><span data-stu-id="1f019-115">Supported Constructs on Natively Compiled Stored Procedures</span></span>](supported-ddl-for-natively-compiled-t-sql-modules.md)  
  
-   [<span data-ttu-id="1f019-116">ネイティブ コンパイル ストアド プロシージャと実行 SET オプション</span><span class="sxs-lookup"><span data-stu-id="1f019-116">Natively Compiled Stored Procedures and Execution Set Options</span></span>](natively-compiled-stored-procedures-and-execution-set-options.md)  
  
-   [<span data-ttu-id="1f019-117">ネイティブ コンパイル ストアド プロシージャの呼び出しに関するベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="1f019-117">Best Practices for Calling Natively Compiled Stored Procedures</span></span>](best-practices-for-calling-natively-compiled-stored-procedures.md)  
  
-   [<span data-ttu-id="1f019-118">ネイティブ コンパイル ストアド プロシージャのパフォーマンスの監視</span><span class="sxs-lookup"><span data-stu-id="1f019-118">Monitoring Performance of Natively Compiled Stored Procedures</span></span>](monitoring-performance-of-natively-compiled-stored-procedures.md)  
  
-   [<span data-ttu-id="1f019-119">データ アクセス アプリケーションからのネイティブ コンパイル ストアド プロシージャの呼び出し</span><span class="sxs-lookup"><span data-stu-id="1f019-119">Calling Natively Compiled Stored Procedures from Data Access Applications</span></span>](calling-natively-compiled-stored-procedures-from-data-access-applications.md)  
  
## <a name="see-also"></a><span data-ttu-id="1f019-120">参照</span><span class="sxs-lookup"><span data-stu-id="1f019-120">See Also</span></span>  
 [<span data-ttu-id="1f019-121">メモリ最適化テーブル</span><span class="sxs-lookup"><span data-stu-id="1f019-121">Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
  

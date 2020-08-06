---
title: ネイティブコンパイルストアドプロシージャでサポートされているコンストラクト |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 6b21f47e-bceb-4054-8b3c-9d39bb9583c0
author: rothja
ms.author: jroth
ms.openlocfilehash: f3bc7e28fa2a868ac39c6adbb2dea3cc5c3ace73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639515"
---
# <a name="supported-constructs-on-natively-compiled-stored-procedures"></a><span data-ttu-id="ef919-102">ネイティブ コンパイル ストアド プロシージャ上でサポートされる構造</span><span class="sxs-lookup"><span data-stu-id="ef919-102">Supported Constructs on Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="ef919-103">このトピックでは、ネイティブ コンパイル ストアド プロシージャでサポートされる構造について説明します。</span><span class="sxs-lookup"><span data-stu-id="ef919-103">This topic lists the supported constructs on natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="ef919-104">サポートされていない構造については、「 [インメモリ OLTP でサポートされていない Transact-SQL の構造](transact-sql-constructs-not-supported-by-in-memory-oltp.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef919-104">For information about unsupported constructs, see [Transact-SQL Constructs Not Supported by In-Memory OLTP](transact-sql-constructs-not-supported-by-in-memory-oltp.md).</span></span>  
  
## <a name="procedure-ddl"></a><span data-ttu-id="ef919-105">プロシージャ DDL</span><span class="sxs-lookup"><span data-stu-id="ef919-105">Procedure DDL</span></span>  
 <span data-ttu-id="ef919-106">サポート対象は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ef919-106">The following are supported:</span></span>  
  
-   <span data-ttu-id="ef919-107">CREATE PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="ef919-107">CREATE PROCEDURE</span></span>  
  
-   <span data-ttu-id="ef919-108">DROP PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="ef919-108">DROP PROCEDURE</span></span>  
  
-   <span data-ttu-id="ef919-109">SCHEMABINDING (ネイティブ コンパイル ストアド プロシージャで必要です)</span><span class="sxs-lookup"><span data-stu-id="ef919-109">SCHEMABINDING (required for natively compiled stored procedures)</span></span>  
  
-   <span data-ttu-id="ef919-110">NATIVE_COMPILATION</span><span class="sxs-lookup"><span data-stu-id="ef919-110">NATIVE_COMPILATION</span></span>  
  
-   <span data-ttu-id="ef919-111">パラメーターは NOT NULL として宣言できます。</span><span class="sxs-lookup"><span data-stu-id="ef919-111">Parameters can be declared as NOT NULL.</span></span>  
  
-   <span data-ttu-id="ef919-112">テーブル値パラメーター</span><span class="sxs-lookup"><span data-stu-id="ef919-112">Table-valued parameters.</span></span>  
  
## <a name="security"></a><span data-ttu-id="ef919-113">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="ef919-113">Security</span></span>  
 <span data-ttu-id="ef919-114">サポート対象は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ef919-114">The following are supported:</span></span>  
  
-   <span data-ttu-id="ef919-115">プロシージャの場合: EXECUTE AS OWNER、SELF、およびユーザー。</span><span class="sxs-lookup"><span data-stu-id="ef919-115">For procedures: EXECUTE AS OWNER, SELF, and user.</span></span>  
  
-   <span data-ttu-id="ef919-116">テーブルおよびプロシージャに対する GRANT 権限および DENY 権限。</span><span class="sxs-lookup"><span data-stu-id="ef919-116">GRANT and DENY permissions on tables and procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef919-117">参照</span><span class="sxs-lookup"><span data-stu-id="ef919-117">See Also</span></span>  
 [<span data-ttu-id="ef919-118">ネイティブ コンパイル ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="ef919-118">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  

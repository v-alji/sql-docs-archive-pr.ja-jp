---
title: データベース エンジン拡張ストアド プロシージャ プログラミング | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], programming
- stored procedures [SQL Server], extended
- Database Engine [SQL Server], stored procedures
- macros [SQL Server]
- Extended Stored Procedure API [SQL Server]
ms.assetid: 158a6765-0542-4e84-b5ab-f173d946ef5e
author: rothja
ms.author: jroth
ms.openlocfilehash: fecb8f996ddfcaede83cdb330e9c82bffdce5819
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645125"
---
# <a name="database-engine-extended-stored-procedure-programming"></a><span data-ttu-id="0dc55-102">データベース エンジン拡張ストアド プロシージャ プログラミング</span><span class="sxs-lookup"><span data-stu-id="0dc55-102">Database Engine Extended Stored Procedure Programming</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="0dc55-103">代わりに CLR Integration を使用してください。</span><span class="sxs-lookup"><span data-stu-id="0dc55-103">Use CLR Integration instead.</span></span> <span data-ttu-id="0dc55-104">詳細については、「[共通言語ランタイム &#40;CLR&#41; 統合のプログラミング概念](clr-integration/common-language-runtime-clr-integration-programming-concepts.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0dc55-104">For more information, see [Common Language Runtime &#40;CLR&#41; Integration Programming Concepts](clr-integration/common-language-runtime-clr-integration-programming-concepts.md).</span></span>  
  
 <span data-ttu-id="0dc55-105">[!INCLUDE[msCoName](../includes/msconame-md.md)]拡張ストアドプロシージャ api には、機能を拡張するためのサーバーベースのアプリケーションプログラミングインターフェイス (api) が用意されて [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] います。</span><span class="sxs-lookup"><span data-stu-id="0dc55-105">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Extended Stored Procedure API provides a server-based application programming interface (API) for extending [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] functionality.</span></span> <span data-ttu-id="0dc55-106">この API は、拡張ストアド プロシージャおよびゲートウェイ アプリケーションのカテゴリでアプリケーションの構築に使用する C および C++ の関数とマクロで構成されています。</span><span class="sxs-lookup"><span data-stu-id="0dc55-106">The API consists of C and C++ functions and macros used to build applications in the following categories: extended stored procedures and gateway applications.</span></span>  
  
 <span data-ttu-id="0dc55-107">拡張ストアド プロシージャを使用すると、C などのプログラミング言語を使用してユーザー独自の外部ルーチンを作成できます。拡張ストアド プロシージャは、ユーザーには通常のストアド プロシージャのように見え、同じように実行されます。</span><span class="sxs-lookup"><span data-stu-id="0dc55-107">Extended stored procedures allow you to create your own external routines in a programming language such as C. The extended stored procedures appear to users as typical stored procedures and are executed in the same way.</span></span> <span data-ttu-id="0dc55-108">拡張ストアド プロシージャにはパラメーターを渡すことができ、拡張ストアド プロシージャは結果や状態を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="0dc55-108">Parameters can be passed to extended stored procedures, and they can return results and return status.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0dc55-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="0dc55-109">In This Section</span></span>  
 [<span data-ttu-id="0dc55-110">拡張ストアド プロシージャのプログラミング</span><span class="sxs-lookup"><span data-stu-id="0dc55-110">Programming Extended Stored Procedures</span></span>](extended-stored-procedures-programming/database-engine-extended-stored-procedures-programming.md)  
 <span data-ttu-id="0dc55-111">拡張ストアド プロシージャを作成、管理、および使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0dc55-111">Explains how to create, manage, and use extended stored procedures.</span></span>  
  
 [<span data-ttu-id="0dc55-112">拡張ストアド プロシージャのプログラマーズ リファレンス</span><span class="sxs-lookup"><span data-stu-id="0dc55-112">Extended Stored Procedures Programmer's Reference</span></span>](extended-stored-procedures-reference/database-engine-extended-stored-procedures-reference.md)  
 <span data-ttu-id="0dc55-113">拡張ストアド プロシージャ API に関する参照トピックが記載されています。</span><span class="sxs-lookup"><span data-stu-id="0dc55-113">Contains reference topics for the Extended Stored Procedure API.</span></span>  
  
  

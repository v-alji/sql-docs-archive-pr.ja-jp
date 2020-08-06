---
title: バイナリラージオブジェクト (Blob) の読み取りと書き込みを行う UPDATETEXT ステートメントを変更します。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- UPDATETEXT statement
- text [SQL Server], UPDATETEXT statements
ms.assetid: b85da6a7-42f6-4707-a25e-3ded8958b94f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 061e7bad0bae5a74d103406265ad79195f79f7db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640433"
---
# <a name="modify-updatetext-statements-that-read-and-write-to-binary-large-objects-blobs"></a><span data-ttu-id="ceb0b-102">バイナリ ラージ オブジェクト (BLOB) を読み書きする UPDATETEXT ステートメントを変更する</span><span class="sxs-lookup"><span data-stu-id="ceb0b-102">Modify UPDATETEXT statements that read and write to binary large objects (BLOBs)</span></span>
  <span data-ttu-id="ceb0b-103">アップグレード アドバイザーによって、同じバイナリ ラージ オブジェクト (BLOB) の読み取りおよび書き込みを実行する UPDATETEXT ステートメントが検出されました。このステートメントでは、同じテキスト ポインターが使用されています。</span><span class="sxs-lookup"><span data-stu-id="ceb0b-103">Upgrade Advisor detected UPDATETEXT statements that read and write to the same binary large objects (BLOB) by using the same text pointer.</span></span> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="ceb0b-104">では、このようなテキスト ポインターの使用方法はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="ceb0b-104">does not support the use of text pointers in this manner.</span></span>  
  
## <a name="component"></a><span data-ttu-id="ceb0b-105">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ceb0b-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="ceb0b-106">修正措置</span><span class="sxs-lookup"><span data-stu-id="ceb0b-106">Corrective Action</span></span>  
 <span data-ttu-id="ceb0b-107">BLOB を一時テーブルまたはテーブル変数にコピーしてから、その値を元の列に割り当ててください。</span><span class="sxs-lookup"><span data-stu-id="ceb0b-107">Copy the BLOB to a temporary table or to a table variable, and then assign the value back to the original column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceb0b-108">参照</span><span class="sxs-lookup"><span data-stu-id="ceb0b-108">See Also</span></span>  
 <span data-ttu-id="ceb0b-109">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="ceb0b-109">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="ceb0b-110">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="ceb0b-110">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  

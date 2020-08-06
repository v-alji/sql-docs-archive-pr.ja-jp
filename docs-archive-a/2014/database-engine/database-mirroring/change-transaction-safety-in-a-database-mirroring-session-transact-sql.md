---
title: データベース ミラーリング セッションでのトランザクションの安全性の変更 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- transaction safety [SQL Server database mirroring]
ms.assetid: 8b03bb82-8589-4558-8545-9942fe008391
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d8bc9d0fb639770d33507c29a6ec67f60bd0434a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634040"
---
# <a name="change-transaction-safety-in-a-database-mirroring-session-transact-sql"></a><span data-ttu-id="28983-102">データベース ミラーリング セッションでのトランザクションの安全性の変更 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="28983-102">Change Transaction Safety in a Database Mirroring Session (Transact-SQL)</span></span>
  <span data-ttu-id="28983-103">トランザクションの安全性は、セッションの動作モードを制御する属性です。</span><span class="sxs-lookup"><span data-stu-id="28983-103">Transaction safety is the attribute that controls the operating mode of the session.</span></span> <span data-ttu-id="28983-104">ただし、データベース所有者は、いつでもトランザクションの安全性を変更できます。</span><span class="sxs-lookup"><span data-stu-id="28983-104">At any time, however, the database owner can change the transaction safety.</span></span> <span data-ttu-id="28983-105">既定では、トランザクションの安全性レベルは FULL (同期動作モード) に設定されています。</span><span class="sxs-lookup"><span data-stu-id="28983-105">By default, the level of transaction safety is set to FULL (synchronous operating mode).</span></span>  
  
 <span data-ttu-id="28983-106">トランザクションの安全性を無効にすると、セッションの動作モードが、パフォーマンスを最適にする非同期動作モードに切り替わります。</span><span class="sxs-lookup"><span data-stu-id="28983-106">Turning off transaction safety shifts the session into asynchronous operating mode, which maximizes performance.</span></span> <span data-ttu-id="28983-107">プリンシパル サーバーを使用できなくなるとミラー サーバーは停止しますが、ミラー サーバーをウォーム スタンバイ サーバーとして使用することができます (フェールオーバーにはサービスの強制が必要ですが、データを損失する可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="28983-107">If the principal becomes unavailable, the mirror stops but is available as a warm standby (failover requires forcing service with possible data loss).</span></span>  
  
### <a name="to-turn-on-transaction-safety"></a><span data-ttu-id="28983-108">トランザクションの安全性を有効にするには</span><span class="sxs-lookup"><span data-stu-id="28983-108">To turn on transaction safety</span></span>  
  
1.  <span data-ttu-id="28983-109">プリンシパル サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="28983-109">Connect to the principal server.</span></span>  
  
2.  <span data-ttu-id="28983-110">次の Transact-SQL ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="28983-110">Issue the following Transact-SQL statement:</span></span>  
  
    ```  
    ALTER DATABASE <database> SET PARTNER SAFETY FULL  
    ```  
  
     <span data-ttu-id="28983-111">ここで、 *\<database>* はミラー化されたデータベースの名前です。</span><span class="sxs-lookup"><span data-stu-id="28983-111">where *\<database>* is the name of the mirrored database.</span></span>  
  
### <a name="to-turn-off-transaction-safety"></a><span data-ttu-id="28983-112">トランザクションの安全性を無効にするには</span><span class="sxs-lookup"><span data-stu-id="28983-112">To turn off transaction safety</span></span>  
  
1.  <span data-ttu-id="28983-113">プリンシパル サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="28983-113">Connect to the principal server.</span></span>  
  
2.  <span data-ttu-id="28983-114">次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="28983-114">Issue the following statement:</span></span>  
  
    ```  
    ALTER DATABASE <database> SET PARTNER SAFETY OFF  
    ```  
  
     <span data-ttu-id="28983-115">ここで、 *\<database>* はミラー化されたデータベースです。</span><span class="sxs-lookup"><span data-stu-id="28983-115">where *\<database>* is the mirrored database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28983-116">参照</span><span class="sxs-lookup"><span data-stu-id="28983-116">See Also</span></span>  
 <span data-ttu-id="28983-117">[ALTER DATABASE データベース ミラーリング &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="28983-117">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 [<span data-ttu-id="28983-118">Database Mirroring Operating Modes</span><span class="sxs-lookup"><span data-stu-id="28983-118">Database Mirroring Operating Modes</span></span>](database-mirroring-operating-modes.md)  
  
  

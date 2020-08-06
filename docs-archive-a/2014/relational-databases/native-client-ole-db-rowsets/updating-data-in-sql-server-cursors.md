---
title: SQL Server カーソルでのデータ更新 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- isolation levels [SQL Server]
- delayed update mode [OLE DB]
- immediate update mode [OLE DB]
- cursors [OLE DB]
- data updates [SQL Server], OLE DB
ms.assetid: 732dafee-f2d5-4aef-aad7-3a8bf3b1e876
author: rothja
ms.author: jroth
ms.openlocfilehash: 42e6221a85c30e3adb97df3a11c9cbdc49216b4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633829"
---
# <a name="updating-data-in-sql-server-cursors"></a><span data-ttu-id="0aa02-102">SQL Server カーソルでのデータ更新</span><span class="sxs-lookup"><span data-stu-id="0aa02-102">Updating Data in SQL Server Cursors</span></span>
  <span data-ttu-id="0aa02-103">カーソルを使用してデータをフェッチおよび更新する場合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native client OLE DB プロバイダーコンシューマーアプリケーションは、他のクライアントアプリケーションに適用されるのと同じ考慮事項と制約によってバインドされます。</span><span class="sxs-lookup"><span data-stu-id="0aa02-103">When fetching and updating data through [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursors, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer application is bound by the same considerations and constraints that apply to any other client application.</span></span>  
  
 <span data-ttu-id="0aa02-104">同時実行データアクセス制御に関係するのは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] カーソル内の行だけです。</span><span class="sxs-lookup"><span data-stu-id="0aa02-104">Only rows in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursors participate in concurrent data-access control.</span></span> <span data-ttu-id="0aa02-105">コンシューマーから変更可能な行セットが要求されるときは、コンカレンシー制御が DBPROP_LOCKMODE によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="0aa02-105">When the consumer requests a modifiable rowset, the concurrency control is controlled by DBPROP_LOCKMODE.</span></span> <span data-ttu-id="0aa02-106">同時実行アクセス制御のレベルを変更するには、コンシューマーで行セットを開く前に DBPROP_LOCKMODE プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="0aa02-106">To modify the level of concurrent access control, the consumer sets the DBPROP_LOCKMODE property before opening the rowset.</span></span>  
  
 <span data-ttu-id="0aa02-107">クライアント アプリケーションのデザインにより、トランザクションが長時間開かれたままの状態になる場合、トランザクション分離レベルが原因で行の位置指定が大幅に遅れる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0aa02-107">Transaction isolation levels can cause significant lags in row positioning if client application design lets transactions remain open for long periods of time.</span></span> <span data-ttu-id="0aa02-108">既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、DBPROPVAL_TI_READCOMMITTED によって指定された read committed 分離レベルを使用します。</span><span class="sxs-lookup"><span data-stu-id="0aa02-108">By default, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider uses the read-committed isolation level specified by DBPROPVAL_TI_READCOMMITTED.</span></span> <span data-ttu-id="0aa02-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、行セットの同時実行が読み取り専用の場合は、ダーティ読み取り分離をサポートします。</span><span class="sxs-lookup"><span data-stu-id="0aa02-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports dirty read isolation when the rowset concurrency is read-only.</span></span> <span data-ttu-id="0aa02-110">そのため、コンシューマーは変更可能な行セットで、より高い分離レベルを要求できますが、より低い分離レベルは要求できません。</span><span class="sxs-lookup"><span data-stu-id="0aa02-110">Therefore, the consumer can request a higher level of isolation in a modifiable rowset but cannot request any lower level successfully.</span></span>  
  
## <a name="immediate-and-delayed-update-modes"></a><span data-ttu-id="0aa02-111">即時更新モードと遅延更新モード</span><span class="sxs-lookup"><span data-stu-id="0aa02-111">Immediate and Delayed Update Modes</span></span>  
 <span data-ttu-id="0aa02-112">即時更新モードでは、**IRowsetChange::SetData** を呼び出すたびに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] との間にラウンドトリップが発生します。</span><span class="sxs-lookup"><span data-stu-id="0aa02-112">In immediate update mode, each call to **IRowsetChange::SetData** causes a round trip to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0aa02-113">コンシューマーが 1 つの行に複数の変更を加える場合は、**SetData** を 1 回呼び出してすべての変更を実行する方が効率が高くなります。</span><span class="sxs-lookup"><span data-stu-id="0aa02-113">If the consumer makes multiple changes to a single row, it is more efficient to submit all changes with a single **SetData** call.</span></span>  
  
 <span data-ttu-id="0aa02-114">遅延更新モードでは、**IRowsetUpdate::Update** の *cRows* パラメーターと *rghRows* パラメーターに示される行ごとに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] との間にラウンドトリップが発生します。</span><span class="sxs-lookup"><span data-stu-id="0aa02-114">In delayed update mode, a roundtrip is made to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for each row indicated in the *cRows* and *rghRows* parameters of **IRowsetUpdate::Update**.</span></span>  
  
 <span data-ttu-id="0aa02-115">どちらのモードでも、行セットに対してトランザクション オブジェクトが開いていないときは、1 つのラウンドトリップが個別のトランザクションを表します。</span><span class="sxs-lookup"><span data-stu-id="0aa02-115">In either mode, a roundtrip represents a distinct transaction when no transaction object is open for the rowset.</span></span>  
  
 <span data-ttu-id="0aa02-116">**IRowsetUpdate:: Update**を使用する場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、指定された各行を処理しようとします。</span><span class="sxs-lookup"><span data-stu-id="0aa02-116">When you are using **IRowsetUpdate::Update**, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider tries to process each indicated row.</span></span> <span data-ttu-id="0aa02-117">行に対して無効なデータ、長さ、または状態の値が原因でエラーが発生しても、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの処理は停止されません。</span><span class="sxs-lookup"><span data-stu-id="0aa02-117">An error occurring because of invalid data, length, or status values for any row does not stop [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider processing.</span></span> <span data-ttu-id="0aa02-118">更新に関係する他のすべての行が変更されることも、そのような行がまったく変更されないこともあります。</span><span class="sxs-lookup"><span data-stu-id="0aa02-118">All or none of the other rows participating in the update may be modified.</span></span> <span data-ttu-id="0aa02-119">コンシューマーは、返された*Prgrowstatus*配列を調べて、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが DB_S_ERRORSOCCURRED を返したときに特定の行のエラーを特定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0aa02-119">The consumer must examine the returned *prgRowStatus* array to determine failure for any specific row when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns DB_S_ERRORSOCCURRED.</span></span>  
  
 <span data-ttu-id="0aa02-120">コンシューマーでは、特定の順序で行が処理されることを想定しないでください。</span><span class="sxs-lookup"><span data-stu-id="0aa02-120">A consumer should not assume that rows are processed in any specific order.</span></span> <span data-ttu-id="0aa02-121">1 行以上の行に対してデータ変更を順序付けて処理することが必要な場合、アプリケーション ロジックで順序を確立し、トランザクションを開いてそのロジックをトランザクション内に含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="0aa02-121">If a consumer requires ordered processing of data modification over more than a single row, the consumer should establish that order in the application logic and open a transaction to enclose the process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aa02-122">参照</span><span class="sxs-lookup"><span data-stu-id="0aa02-122">See Also</span></span>  
 [<span data-ttu-id="0aa02-123">行セット内のデータの更新</span><span class="sxs-lookup"><span data-stu-id="0aa02-123">Updating Data in Rowsets</span></span>](updating-data-in-rowsets.md)  
  
  

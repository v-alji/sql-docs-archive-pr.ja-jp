---
title: 分離レベル (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: d70ee72c-6e2a-4bcd-9456-4a697a866361
author: rothja
ms.author: jroth
ms.openlocfilehash: c7f6cbff4e68eaedd3e78a82cddd872ba5f8f19e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642042"
---
# <a name="isolation-levels-ole-db"></a><span data-ttu-id="2b969-102">分離レベル (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="2b969-102">Isolation Levels (OLE DB)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2b969-103">クライアントは、接続のトランザクション分離レベルを制御できます。</span><span class="sxs-lookup"><span data-stu-id="2b969-103">clients can control transaction-isolation levels for a connection.</span></span> <span data-ttu-id="2b969-104">トランザクション分離レベルを制御するために、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーコンシューマーは次のものを使用します。</span><span class="sxs-lookup"><span data-stu-id="2b969-104">To control transaction-isolation level, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer uses:</span></span>  
  
-   <span data-ttu-id="2b969-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーの既定の自動コミットモードの DBPROPSET_SESSION プロパティ DBPROP_SESS_AUTOCOMMITISOLEVELS。</span><span class="sxs-lookup"><span data-stu-id="2b969-105">DBPROPSET_SESSION property DBPROP_SESS_AUTOCOMMITISOLEVELS for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider default autocommit mode.</span></span>  
  
     <span data-ttu-id="2b969-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]レベルの Native Client OLE DB プロバイダーの既定値は DBPROPVAL_TI_READCOMMITTED です。</span><span class="sxs-lookup"><span data-stu-id="2b969-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider default for the level is DBPROPVAL_TI_READCOMMITTED.</span></span>  
  
-   <span data-ttu-id="2b969-107">ローカルの手動コミット トランザクションには、**ITransactionLocal::StartTransaction** メソッドの *isoLevel* パラメーター。</span><span class="sxs-lookup"><span data-stu-id="2b969-107">The *isoLevel* parameter of the **ITransactionLocal::StartTransaction** method for local manual-commit transactions.</span></span>  
  
-   <span data-ttu-id="2b969-108">MS DTC でコーディネートされる分散トランザクションには、**ITransactionDispenser::BeginTransaction** メソッドの *isoLevel* パラメーター。</span><span class="sxs-lookup"><span data-stu-id="2b969-108">The *isoLevel* parameter of the **ITransactionDispenser::BeginTransaction** method for MS DTC-coordinated distributed transactions.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2b969-109">では、ダーティ リード分離レベルでの読み取り専用アクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="2b969-109">allows read-only access at the dirty read isolation level.</span></span> <span data-ttu-id="2b969-110">他のすべてのレベルでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトにロックをかけることによってコンカレンシーを制限します。</span><span class="sxs-lookup"><span data-stu-id="2b969-110">All other levels restrict concurrency by applying locks to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objects.</span></span> <span data-ttu-id="2b969-111">クライアントがより高度なコンカレンシー レベルを要求すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はデータへのコンカレント アクセスに対してより厳密な制限を適用します。</span><span class="sxs-lookup"><span data-stu-id="2b969-111">As the client requires greater concurrency levels, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] applies greater restrictions on concurrent access to data.</span></span> <span data-ttu-id="2b969-112">データへの最大レベルの同時アクセスを維持するために、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーコンシューマーは、特定の同時実行レベルに対する要求をインテリジェントに制御する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b969-112">To maintain the highest level of concurrent access to data, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer should intelligently control its requests for specific concurrency levels.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="2b969-113">ではスナップショット分離レベルが導入されました。</span><span class="sxs-lookup"><span data-stu-id="2b969-113">introduced snapshot isolation level.</span></span> <span data-ttu-id="2b969-114">詳細については、「[スナップショット分離を使用した作業](../native-client/features/working-with-snapshot-isolation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b969-114">For more information, see [Working with Snapshot Isolation](../native-client/features/working-with-snapshot-isolation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b969-115">参照</span><span class="sxs-lookup"><span data-stu-id="2b969-115">See Also</span></span>  
 [<span data-ttu-id="2b969-116">トランザクション</span><span class="sxs-lookup"><span data-stu-id="2b969-116">Transactions</span></span>](transactions.md)  
  
  

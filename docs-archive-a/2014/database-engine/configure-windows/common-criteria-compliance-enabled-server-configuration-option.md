---
title: common criteria compliance enabled サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- common criteria compliance
helpviewer_keywords:
- CC (common criteria) [Database Engine]
- common criteria compliance [Database Engine]
- Risidual Information Protection [Database Engine]
- RIP (Residual Information Protection)
ms.assetid: 61766eea-c450-408d-af33-fbe7ef8c9ff2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6722d05351b8b9e80240abb4edef0633a97b6da0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632110"
---
# <a name="common-criteria-compliance-enabled-server-configuration-option"></a><span data-ttu-id="6cf8f-102">common criteria compliance enabled サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="6cf8f-102">common criteria compliance enabled Server Configuration Option</span></span>
  <span data-ttu-id="6cf8f-103">[情報セキュリティ国際評価基準 (Common Criteria) への準拠を有効にする] オプションを使用すると、情報セキュリティ国際評価基準で必要とされる次の要素を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="6cf8f-103">The common criteria compliance enabled option enables the following elements that are required for the Common Criteria.</span></span>  
  
|<span data-ttu-id="6cf8f-104">条件</span><span class="sxs-lookup"><span data-stu-id="6cf8f-104">Criteria</span></span>|<span data-ttu-id="6cf8f-105">説明</span><span class="sxs-lookup"><span data-stu-id="6cf8f-105">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="6cf8f-106">残存情報保護 (RIP)</span><span class="sxs-lookup"><span data-stu-id="6cf8f-106">Residual Information Protection (RIP)</span></span>|<span data-ttu-id="6cf8f-107">RIP の要件とは、新しいリソースにメモリを再度割り当てる前に、メモリ割り当てを既知のビット パターンで上書きすることです。</span><span class="sxs-lookup"><span data-stu-id="6cf8f-107">RIP requires a memory allocation to be overwritten with a known pattern of bits before memory is reallocated to a new resource.</span></span> <span data-ttu-id="6cf8f-108">RIP 標準を満たすとセキュリティの向上が図れますが、メモリ割り当てを上書きすることによってパフォーマンスが低下する場合があります。</span><span class="sxs-lookup"><span data-stu-id="6cf8f-108">Meeting the RIP standard can contribute to improved security; however, overwriting the memory allocation can slow performance.</span></span> <span data-ttu-id="6cf8f-109">[情報セキュリティ国際評価基準 (Common Criteria) への準拠を有効にする] を有効にすると、この上書きが行われます。</span><span class="sxs-lookup"><span data-stu-id="6cf8f-109">After the common criteria compliance enabled option is enabled, the overwriting occurs.</span></span>|  
|<span data-ttu-id="6cf8f-110">ログインの統計を表示する機能</span><span class="sxs-lookup"><span data-stu-id="6cf8f-110">The ability to view login statistics</span></span>|<span data-ttu-id="6cf8f-111">[情報セキュリティ国際評価基準 (Common Criteria) への準拠を有効にする] を有効にすると、ログイン監査が有効になります。</span><span class="sxs-lookup"><span data-stu-id="6cf8f-111">After the common criteria compliance enabled option is enabled, login auditing is enabled.</span></span> <span data-ttu-id="6cf8f-112">ユーザーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]へのログインに成功するたびに、最後にログインに成功した時間、最後にログインに失敗した時間、最後にログインした時間から現在のログイン時間までのログイン試行回数について、情報を確認できます。</span><span class="sxs-lookup"><span data-stu-id="6cf8f-112">Each time a user successfully logs in to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], information about the last successful login time, the last unsuccessful login time, and the number of attempts between the last successful and current login times is made available.</span></span> <span data-ttu-id="6cf8f-113">このログインに関する統計情報は、 [sys.dm_exec_sessions](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) 動的管理ビューにクエリを実行すると表示できます。</span><span class="sxs-lookup"><span data-stu-id="6cf8f-113">These login statistics can be viewed by querying the [sys.dm_exec_sessions](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) dynamic management view.</span></span>|  
|<span data-ttu-id="6cf8f-114">列の GRANT がテーブルの DENY をオーバーライドしないこと</span><span class="sxs-lookup"><span data-stu-id="6cf8f-114">That column GRANT should not override table DENY</span></span>|<span data-ttu-id="6cf8f-115">[情報セキュリティ国際評価基準 (Common Criteria) への準拠を有効にする] を有効にすると、テーブル レベルの DENY が列レベルの GRANT より優先されます。</span><span class="sxs-lookup"><span data-stu-id="6cf8f-115">After the common criteria compliance enabled option is enabled, a table-level DENY takes precedence over a column-level GRANT.</span></span> <span data-ttu-id="6cf8f-116">このオプションが有効でない場合は、列レベルの GRANT がテーブル レベルの DENY より優先されます。</span><span class="sxs-lookup"><span data-stu-id="6cf8f-116">When the option is not enabled, a column-level GRANT takes precedence over a table-level DENY.</span></span>|  
  
 <span data-ttu-id="6cf8f-117">[Common Criteria Compliance Enabled] オプションは拡張オプションです。</span><span class="sxs-lookup"><span data-stu-id="6cf8f-117">The common criteria compliance enabled option is an advanced option.</span></span> <span data-ttu-id="6cf8f-118">情報セキュリティ国際評価基準は、Enterprise Edition と Datacenter Edition についてのみ評価され、認定されています。</span><span class="sxs-lookup"><span data-stu-id="6cf8f-118">Common criteria is only evaluated and certified for the Enterprise edition and Datacenter edition.</span></span> <span data-ttu-id="6cf8f-119">情報セキュリティ国際評価基準の最新の状況については、 [Microsoft SQL Server の情報セキュリティ国際評価基準](https://go.microsoft.com/fwlink/?LinkId=616319) の Web サイトを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6cf8f-119">For the latest status of common criteria certification, see the [Microsoft SQL Server Common Criteria](https://go.microsoft.com/fwlink/?LinkId=616319) Web site.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6cf8f-120">情報セキュリティ国際評価基準の評価保証レベル 4+ (EAL4+) に準拠するには、[情報セキュリティ国際評価基準 (Common Criteria) への準拠を有効にする] オプションを有効にすることのほかに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の構成を完了するためのスクリプトをダウンロードして実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6cf8f-120">In addition to enabling the common criteria compliance enabled option, you also must download and run a script that finishes configuring [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to comply with Common Criteria Evaluation Assurance Level 4+ (EAL4+).</span></span> <span data-ttu-id="6cf8f-121">このスクリプトは、 [Microsoft SQL Server 情報セキュリティ国際評価基準](https://go.microsoft.com/fwlink/?LinkId=616319) Web サイトからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="6cf8f-121">You can download this script from the [Microsoft SQL Server Common Criteria](https://go.microsoft.com/fwlink/?LinkId=616319) Web site.</span></span>  
  
 <span data-ttu-id="6cf8f-122">sp_configure システム ストアド プロシージャを使用してこの設定を変更する場合、[情報セキュリティ国際評価基準 (Common Criteria) への準拠を有効にする] を変更できるのは、show advanced options が 1 に設定されているときだけです。</span><span class="sxs-lookup"><span data-stu-id="6cf8f-122">If you are using the sp_configure system stored procedure to change the setting, you can change common criteria compliance enabled only when show advanced options is set to 1.</span></span> <span data-ttu-id="6cf8f-123">この設定は、サーバーを再起動した後に有効になります。</span><span class="sxs-lookup"><span data-stu-id="6cf8f-123">The setting takes effect after the server is restarted.</span></span> <span data-ttu-id="6cf8f-124">有効値は、0 および 1 です。</span><span class="sxs-lookup"><span data-stu-id="6cf8f-124">The possible values are 0 and 1:</span></span>  
  
-   <span data-ttu-id="6cf8f-125">0 は [情報セキュリティ国際評価基準 (Common Criteria) への準拠を有効にする] が有効でないことを表します。</span><span class="sxs-lookup"><span data-stu-id="6cf8f-125">0 indicates that common criteria compliance is not enabled.</span></span> <span data-ttu-id="6cf8f-126">これは既定値です。</span><span class="sxs-lookup"><span data-stu-id="6cf8f-126">This is the default.</span></span>  
  
-   <span data-ttu-id="6cf8f-127">1 は [情報セキュリティ国際評価基準 (Common Criteria) への準拠を有効にする] が有効であることを表します。</span><span class="sxs-lookup"><span data-stu-id="6cf8f-127">1 indicates that common criteria compliance is enabled.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="6cf8f-128">例</span><span class="sxs-lookup"><span data-stu-id="6cf8f-128">Examples</span></span>  
 <span data-ttu-id="6cf8f-129">次の例では、情報セキュリティ国際評価基準への準拠を有効にしています。</span><span class="sxs-lookup"><span data-stu-id="6cf8f-129">The following example enables common criteria compliance.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'common criteria compliance enabled', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="6cf8f-130">参照</span><span class="sxs-lookup"><span data-stu-id="6cf8f-130">See Also</span></span>  
 [<span data-ttu-id="6cf8f-131">サーバー構成オプション &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6cf8f-131">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  

---
title: ad hoc distributed queries サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- OPENROWSET function, ad hoc distributed queries option
- Ad Hoc Distributed Queries option
- ad hoc distributed queries
- 7415 (Database Engine Error)
- OPENDATASOURCE function, ad hoc distributed queries option
- ad hoc access
ms.assetid: 5b982015-e196-44c3-83b8-275fb9d769b2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d07b3c038597916cdaf026e24e90aab9d6b61616
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631241"
---
# <a name="ad-hoc-distributed-queries-server-configuration-option"></a><span data-ttu-id="8a605-102">ad hoc distributed queries サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="8a605-102">ad hoc distributed queries Server Configuration Option</span></span>
  <span data-ttu-id="8a605-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定では、OPENROWSET および OPENDATASOURCE を使用したアドホックな分散クエリは実行できません。</span><span class="sxs-lookup"><span data-stu-id="8a605-103">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not allow ad hoc distributed queries using OPENROWSET and OPENDATASOURCE.</span></span> <span data-ttu-id="8a605-104">このオプションを 1 に設定すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でアドホック アクセスを実行できます。</span><span class="sxs-lookup"><span data-stu-id="8a605-104">When this option is set to 1, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] allows ad hoc access.</span></span> <span data-ttu-id="8a605-105">このオプションを設定しなかった場合または 0 に設定した場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でアドホック アクセスを実行できません。</span><span class="sxs-lookup"><span data-stu-id="8a605-105">When this option is not set or is set to 0, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not allow ad hoc access.</span></span>  
  
 <span data-ttu-id="8a605-106">アドホック分散クエリの実行時には、OLE DB を使用するリモート データ ソースへの接続に OPENROWSET 関数および OPENDATASOURCE 関数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="8a605-106">Ad hoc distributed queries use the OPENROWSET and OPENDATASOURCE functions to connect to remote data sources that use OLE DB.</span></span> <span data-ttu-id="8a605-107">OPENROWSET 関数および OPENDATASOURCE 関数は、アクセス頻度の低い OLE DB データ ソースを参照する目的のみに使用してください。</span><span class="sxs-lookup"><span data-stu-id="8a605-107">OPENROWSET and OPENDATASOURCE should be used only to reference OLE DB data sources that are accessed infrequently.</span></span> <span data-ttu-id="8a605-108">何度もアクセスするデータ ソースに対しては、リンク サーバーを定義してください。</span><span class="sxs-lookup"><span data-stu-id="8a605-108">For any data sources that will be accessed more than several times, define a linked server.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8a605-109">アドホック名を使用できるようにすると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への認証済みログインであればプロバイダーにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="8a605-109">Enabling the use of ad hoc names means that any authenticated login to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can access the provider.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8a605-110">の管理者は、ローカル ログインからアクセスされても安全なプロバイダーに対してのみ、この機能を有効にしてください。</span><span class="sxs-lookup"><span data-stu-id="8a605-110">administrators should enable this feature for providers that are safe to be accessed by any local login.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a605-111">解説</span><span class="sxs-lookup"><span data-stu-id="8a605-111">Remarks</span></span>  
 <span data-ttu-id="8a605-112">**アドホック分散クエリ**を有効にせずにアドホック接続を試みると、次のエラーが発生します: メッセージ 7415、レベル 16、状態 1、行 1</span><span class="sxs-lookup"><span data-stu-id="8a605-112">Attempting to make an ad hoc connection with **Ad Hoc Distributed Queries** not enabled results in error: Msg 7415, Level 16, State 1, Line 1</span></span>  
  
 <span data-ttu-id="8a605-113">OLE DB プロバイダー 'Microsoft.ACE.OLEDB.12.0' へのアドホック アクセスが拒否されました。</span><span class="sxs-lookup"><span data-stu-id="8a605-113">Ad hoc access to OLE DB provider 'Microsoft.ACE.OLEDB.12.0' has been denied.</span></span> <span data-ttu-id="8a605-114">リンク サーバー経由でこのプロバイダーにアクセスしてください。</span><span class="sxs-lookup"><span data-stu-id="8a605-114">You must access this provider through a linked server.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="8a605-115">例</span><span class="sxs-lookup"><span data-stu-id="8a605-115">Examples</span></span>  
 <span data-ttu-id="8a605-116">次の例では、アドホック分散クエリを有効にし、 `Seattle1` 関数を使用して `OPENROWSET` という名前のサーバーにクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="8a605-116">The following example enables ad hoc distributed queries and then queries a server named `Seattle1` using the `OPENROWSET` function.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
RECONFIGURE;  
sp_configure 'Ad Hoc Distributed Queries', 1;  
RECONFIGURE;  
GO  
  
SELECT a.*  
FROM OPENROWSET('SQLNCLI', 'Server=Seattle1;Trusted_Connection=yes;',  
     'SELECT GroupName, Name, DepartmentID  
      FROM AdventureWorks2012.HumanResources.Department  
      ORDER BY GroupName, Name') AS a;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="8a605-117">参照</span><span class="sxs-lookup"><span data-stu-id="8a605-117">See Also</span></span>  
 <span data-ttu-id="8a605-118">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8a605-118">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="8a605-119">[リンク サーバー &#40;データベース エンジン&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="8a605-119">[Linked Servers &#40;Database Engine&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md) </span></span>  
 <span data-ttu-id="8a605-120">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8a605-120">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="8a605-121">[OPENDATASOURCE &#40;Transact-SQL&#41;](/sql/t-sql/functions/opendatasource-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8a605-121">[OPENDATASOURCE &#40;Transact-SQL&#41;](/sql/t-sql/functions/opendatasource-transact-sql) </span></span>  
 [<span data-ttu-id="8a605-122">sp_addlinkedserver &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8a605-122">sp_addlinkedserver &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)  
  
  

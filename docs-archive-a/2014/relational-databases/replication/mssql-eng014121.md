---
title: MSSQL_ENG014121 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014121 error
ms.assetid: c8595854-cce1-4566-ad64-d565555caded
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 04d4cbdd2197745d2d795814d88c4f7bc28eb90e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630931"
---
# <a name="mssql_eng014121"></a><span data-ttu-id="3bb98-102">MSSQL_ENG014121</span><span class="sxs-lookup"><span data-stu-id="3bb98-102">MSSQL_ENG014121</span></span>
    
## <a name="message-details"></a><span data-ttu-id="3bb98-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="3bb98-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3bb98-104">製品名</span><span class="sxs-lookup"><span data-stu-id="3bb98-104">Product Name</span></span>|<span data-ttu-id="3bb98-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="3bb98-105">SQL Server</span></span>|  
|<span data-ttu-id="3bb98-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3bb98-106">Event ID</span></span>|<span data-ttu-id="3bb98-107">14121</span><span class="sxs-lookup"><span data-stu-id="3bb98-107">14121</span></span>|  
|<span data-ttu-id="3bb98-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="3bb98-108">Event Source</span></span>|<span data-ttu-id="3bb98-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="3bb98-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="3bb98-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="3bb98-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="3bb98-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="3bb98-111">Symbolic Name</span></span>||  
|<span data-ttu-id="3bb98-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="3bb98-112">Message Text</span></span>|<span data-ttu-id="3bb98-113">ディストリビューター '%s' を削除できませんでした。</span><span class="sxs-lookup"><span data-stu-id="3bb98-113">Could not drop the Distributor '%s'.</span></span> <span data-ttu-id="3bb98-114">このディストリビューターはディストリビューション データベースに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="3bb98-114">This Distributor has associated distribution databases.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3bb98-115">説明</span><span class="sxs-lookup"><span data-stu-id="3bb98-115">Explanation</span></span>  
 <span data-ttu-id="3bb98-116">ディストリビューターとして構成されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに関連付けられているディストリビューション データベースがあるため、そのインスタンスをディストリビューター ロールから削除できません。</span><span class="sxs-lookup"><span data-stu-id="3bb98-116">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that is configured as a Distributor cannot be removed from the role of Distributor because there are distribution databases associated with the instance.</span></span> <span data-ttu-id="3bb98-117">このエラーは、1 つ以上のパブリッシャーに関連付けられているディストリビューション データベースを削除しようとした場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="3bb98-117">This error occurs if you attempt to drop a distribution database that is associated with one or more Publishers.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3bb98-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="3bb98-118">User Action</span></span>  
 <span data-ttu-id="3bb98-119">このディストリビューターに関連付けられているパブリッシャーおよびディストリビューション データベースの名前を調べるには、ディストリビューター上の任意のデータベースで [sp_helpdistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="3bb98-119">To find the names of any Publishers and distribution databases associated with this Distributor, execute [sp_helpdistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql) from any database on the Distributor.</span></span>  
  
 <span data-ttu-id="3bb98-120">このディストリビューターに関連付けられているすべてのディストリビューション データベースに対し、[sp_dropdistributiondb &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="3bb98-120">Execute [sp_dropdistributiondb &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql) for any distribution databases associated with this Distributor.</span></span> <span data-ttu-id="3bb98-121">ディストリビューション データベースの関連付けをすべて削除すると、ディストリビューションを無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="3bb98-121">After all distribution database associations are removed, you can disable distribution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bb98-122">参照</span><span class="sxs-lookup"><span data-stu-id="3bb98-122">See Also</span></span>  
 <span data-ttu-id="3bb98-123">[エラーとイベントのリファレンス &#40;レプリケーション&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="3bb98-123">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 <span data-ttu-id="3bb98-124">[[ディストリビューションの構成]](configure-distribution.md)</span><span class="sxs-lookup"><span data-stu-id="3bb98-124">[Configure Distribution](configure-distribution.md)</span></span>  
  
  

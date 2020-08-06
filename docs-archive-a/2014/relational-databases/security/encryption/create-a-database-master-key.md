---
title: データベース マスター キーの作成 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2019
ms.prod: sql-server-2014
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], creating
ms.assetid: 8cb24263-e97d-4e4d-9429-6cf494a4d5eb
author: jaszymas
ms.author: jaszymas
ms.reviewer: carlrab
ms.openlocfilehash: cb8305d9d5a3c72e6dffafd231f21110a5abdd14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741717"
---
# <a name="create-a-database-master-key"></a><span data-ttu-id="587c4-102">データベース マスター キーの作成</span><span class="sxs-lookup"><span data-stu-id="587c4-102">Create a Database Master Key</span></span>

<span data-ttu-id="587c4-103">このトピックでは、でを使用して、データベースにデータベースマスターキーを作成する方法について説明し `master` [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] [!INCLUDE[tsql](../../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="587c4-103">This topic describes how to create a database master key in the `master` database in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>

<span data-ttu-id="587c4-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="587c4-104">**In This Topic**</span></span>

- <span data-ttu-id="587c4-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="587c4-105">**Before you begin:**</span></span>

  [<span data-ttu-id="587c4-106">Security</span><span class="sxs-lookup"><span data-stu-id="587c4-106">Security</span></span>](#Security)

- [<span data-ttu-id="587c4-107">Transact-SQL を使用してデータベース マスター キーを作成するには</span><span class="sxs-lookup"><span data-stu-id="587c4-107">To create a database master key using Transact-SQL</span></span>](#TsqlProcedure)

## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="587c4-108">はじめに</span><span class="sxs-lookup"><span data-stu-id="587c4-108">Before You Begin</span></span>

### <a name="security"></a><a name="Security"></a> <span data-ttu-id="587c4-109">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="587c4-109">Security</span></span>

#### <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="587c4-110">Permissions</span><span class="sxs-lookup"><span data-stu-id="587c4-110">Permissions</span></span>

<span data-ttu-id="587c4-111">データベースに対する CONTROL 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="587c4-111">Requires CONTROL permission on the database.</span></span>

## <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="587c4-112">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="587c4-112">Using Transact-SQL</span></span>

### <a name="to-create-a-database-master-key"></a><span data-ttu-id="587c4-113">データベース マスター キーを作成するには</span><span class="sxs-lookup"><span data-stu-id="587c4-113">To create a database master key</span></span>

1. <span data-ttu-id="587c4-114">データベースに格納するマスター キーのコピーを暗号化するためのパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="587c4-114">Choose a password for encrypting the copy of the master key that will be stored in the database.</span></span>
2. <span data-ttu-id="587c4-115">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="587c4-115">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>
3. <span data-ttu-id="587c4-116">**[システム データベース]** を展開し、`master` を右クリックして、 **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="587c4-116">Expand **System Databases**, right-click `master` and then click **New Query**.</span></span>
4. <span data-ttu-id="587c4-117">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="587c4-117">Copy and paste the following example into the query window and click **Execute**.</span></span>

  ```sql
  -- Creates the master key.
  -- The key is encrypted using the password "23987hxJ#KL95234nl0zBe."
  CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';
```

<span data-ttu-id="587c4-118">詳細については、[CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="587c4-118">For more information, see [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql).</span></span>

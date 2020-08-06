---
title: SQL Server Compact Edition 接続マネージャーエディター ([すべて] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlmobileconnection.all.f1
helpviewer_keywords:
- SQL Server Compact Connection Manager Editor
ms.assetid: f9fbff4b-c502-44b3-8e7b-398d66e82206
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4f881d63de5435426475c3aed4b666870d706b40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639553"
---
# <a name="sql-server-compact-edition-connection-manager-editor-all-page"></a><span data-ttu-id="b4fb8-102">[SQL Server Compact Edition 接続マネージャー エディター] ([すべて] ページ)</span><span class="sxs-lookup"><span data-stu-id="b4fb8-102">SQL Server Compact Edition Connection Manager Editor (All Page)</span></span>
  <span data-ttu-id="b4fb8-103">**[SQL Server Compact Edition 接続マネージャー エディター]** ダイアログ ボックスでは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact データベースに接続するためのプロパティを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b4fb8-103">Use the **SQL Server Compact Edition Connection Manager** dialog box to specify properties for connecting to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
 <span data-ttu-id="b4fb8-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact Edition 接続マネージャーについて詳しくは、「 [SQL Server Compact Edition 接続マネージャー](connection-manager/sql-server-compact-edition-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b4fb8-104">To learn more about the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact Edition connection manager, see [SQL Server Compact Edition Connection Manager](connection-manager/sql-server-compact-edition-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="b4fb8-105">Options</span><span class="sxs-lookup"><span data-stu-id="b4fb8-105">Options</span></span>  
 <span data-ttu-id="b4fb8-106">**[AutoShrink Threshold]**</span><span class="sxs-lookup"><span data-stu-id="b4fb8-106">**AutoShrink Threshold**</span></span>  
 <span data-ttu-id="b4fb8-107">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact データベース ファイルの空き容量 (%) がどの程度になったら自動圧縮プロセスを実行するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b4fb8-107">Specify the amount of free space, as a percentage, that is allowed in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database before the autoshrink process runs.</span></span>  
  
 <span data-ttu-id="b4fb8-108">**[Default Lock Escalation]**</span><span class="sxs-lookup"><span data-stu-id="b4fb8-108">**Default Lock Escalation**</span></span>  
 <span data-ttu-id="b4fb8-109">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact データベースが、ロックのエスカレートを試行する前に取得するデータベース ロックの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="b4fb8-109">Specify the number of database locks that the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database acquires before it tries to escalate locks.</span></span>  
  
 <span data-ttu-id="b4fb8-110">**[Default Lock Timeout]**</span><span class="sxs-lookup"><span data-stu-id="b4fb8-110">**Default Lock Timeout**</span></span>  
 <span data-ttu-id="b4fb8-111">トランザクションがロックを待機する既定の間隔を、ミリ秒単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="b4fb8-111">Specify the default interval, in milliseconds, that a transaction will wait for a lock.</span></span>  
  
 <span data-ttu-id="b4fb8-112">**[Flush Interval]**</span><span class="sxs-lookup"><span data-stu-id="b4fb8-112">**Flush Interval**</span></span>  
 <span data-ttu-id="b4fb8-113">トランザクションがコミットされてから、ディスクにフラッシュされるまでの間隔を秒単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="b4fb8-113">Specify the interval, in seconds, between committed transactions to flush data to disk.</span></span>  
  
 <span data-ttu-id="b4fb8-114">**[Locale Identifier]**</span><span class="sxs-lookup"><span data-stu-id="b4fb8-114">**Locale Identifier**</span></span>  
 <span data-ttu-id="b4fb8-115">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact データベースのロケール ID (LCID) を指定します。</span><span class="sxs-lookup"><span data-stu-id="b4fb8-115">Specify the Locale ID (LCID) of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
 <span data-ttu-id="b4fb8-116">**[Max Buffer Size]**</span><span class="sxs-lookup"><span data-stu-id="b4fb8-116">**Max Buffer Size**</span></span>  
 <span data-ttu-id="b4fb8-117">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact が、データをディスクにフラッシュするまでに使用する最大メモリ容量を KB 単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="b4fb8-117">Specify the maximum amount of memory, in kilobytes, that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact uses before flushing data to disk.</span></span>  
  
 <span data-ttu-id="b4fb8-118">**最大データベースサイズ**</span><span class="sxs-lookup"><span data-stu-id="b4fb8-118">**Max Database Size**</span></span>  
 <span data-ttu-id="b4fb8-119">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact データベースの最大サイズを MB 単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="b4fb8-119">Specify the maximum size, in megabytes, of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
 <span data-ttu-id="b4fb8-120">**モード**</span><span class="sxs-lookup"><span data-stu-id="b4fb8-120">**Mode**</span></span>  
 <span data-ttu-id="b4fb8-121">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact データベースを開くファイル モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="b4fb8-121">Specify the file mode in which to open the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database.</span></span> <span data-ttu-id="b4fb8-122">このプロパティの既定値は **[Read Write]** です。</span><span class="sxs-lookup"><span data-stu-id="b4fb8-122">The default value for this property is **Read Write**.</span></span>  
  
 <span data-ttu-id="b4fb8-123">[Mode] オプションには、次の表に示すように 4 つの値が用意されています。</span><span class="sxs-lookup"><span data-stu-id="b4fb8-123">The Mode option has four values, as described in the following table.</span></span>  
  
|<span data-ttu-id="b4fb8-124">値</span><span class="sxs-lookup"><span data-stu-id="b4fb8-124">Value</span></span>|<span data-ttu-id="b4fb8-125">説明</span><span class="sxs-lookup"><span data-stu-id="b4fb8-125">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b4fb8-126">**読み取り専用**</span><span class="sxs-lookup"><span data-stu-id="b4fb8-126">**Read Only**</span></span>|<span data-ttu-id="b4fb8-127">データベースに対する読み取り専用アクセスを指定します。</span><span class="sxs-lookup"><span data-stu-id="b4fb8-127">Specifies read-only access to the database.</span></span>|  
|<span data-ttu-id="b4fb8-128">**読み取り/書き込み**</span><span class="sxs-lookup"><span data-stu-id="b4fb8-128">**Read Write**</span></span>|<span data-ttu-id="b4fb8-129">データベースに対する読み取り/書き込み権限を指定します。</span><span class="sxs-lookup"><span data-stu-id="b4fb8-129">Specifies read/write permission to the database.</span></span>|  
|<span data-ttu-id="b4fb8-130">**[排他]**</span><span class="sxs-lookup"><span data-stu-id="b4fb8-130">**Exclusive**</span></span>|<span data-ttu-id="b4fb8-131">データベースに対する排他アクセスを指定します。</span><span class="sxs-lookup"><span data-stu-id="b4fb8-131">Specifies exclusive access to the database.</span></span>|  
|<span data-ttu-id="b4fb8-132">**[Shared Read]**</span><span class="sxs-lookup"><span data-stu-id="b4fb8-132">**Shared Read**</span></span>|<span data-ttu-id="b4fb8-133">他のユーザーがデータベースからの読み取りを同時に行うことができることを指定します。</span><span class="sxs-lookup"><span data-stu-id="b4fb8-133">Specifies that other users can read from the database at the same time.</span></span>|  
  
 <span data-ttu-id="b4fb8-134">**Persist Security Info**</span><span class="sxs-lookup"><span data-stu-id="b4fb8-134">**Persist Security Info**</span></span>  
 <span data-ttu-id="b4fb8-135">セキュリティ情報を接続文字列の一部として返すかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b4fb8-135">Specify whether security information is returned as part of the connection string.</span></span> <span data-ttu-id="b4fb8-136">このオプションの既定値は**False**です。</span><span class="sxs-lookup"><span data-stu-id="b4fb8-136">The default value for this option is **False**.</span></span>  
  
 <span data-ttu-id="b4fb8-137">**[Temp File Directory]**</span><span class="sxs-lookup"><span data-stu-id="b4fb8-137">**Temp File Directory**</span></span>  
 <span data-ttu-id="b4fb8-138">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 一時データベース ファイルの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="b4fb8-138">Specify the location of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact temporary database file.</span></span>  
  
 <span data-ttu-id="b4fb8-139">**データ ソース**</span><span class="sxs-lookup"><span data-stu-id="b4fb8-139">**Data Source**</span></span>  
 <span data-ttu-id="b4fb8-140">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact データベースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="b4fb8-140">Specify the name of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
 <span data-ttu-id="b4fb8-141">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="b4fb8-141">**Password**</span></span>  
 <span data-ttu-id="b4fb8-142">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact データベースのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="b4fb8-142">Enter the password for the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4fb8-143">参照</span><span class="sxs-lookup"><span data-stu-id="b4fb8-143">See Also</span></span>  
 <span data-ttu-id="b4fb8-144">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="b4fb8-144">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="b4fb8-145">[[SQL Server Compact Edition 接続マネージャー エディター] &#40;[接続] ページ&#41;](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-connection-page.md)</span><span class="sxs-lookup"><span data-stu-id="b4fb8-145">[SQL Server Compact Edition Connection Manager Editor &#40;Connection Page&#41;](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-connection-page.md)</span></span>  
  
  

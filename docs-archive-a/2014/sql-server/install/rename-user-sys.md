---
title: ユーザー sys | の名前を変更します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sys user names [SQL Server]
ms.assetid: d622d646-83e4-4b6f-9a21-77b301af04b5
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3af9d31a54adc5645cab6fcc7104ae7ff27a61b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631497"
---
# <a name="rename-user-sys"></a><span data-ttu-id="c431c-102">ユーザー sys の名前変更が必要</span><span class="sxs-lookup"><span data-stu-id="c431c-102">Rename user sys</span></span>
  <span data-ttu-id="c431c-103">アップグレードアドバイザーによって、データベースにユーザー名**sys**が検出されました。</span><span class="sxs-lookup"><span data-stu-id="c431c-103">Upgrade Advisor detected the user name **sys** in a database.</span></span> <span data-ttu-id="c431c-104">この名前は予約されています。</span><span class="sxs-lookup"><span data-stu-id="c431c-104">This name is reserved.</span></span> <span data-ttu-id="c431c-105">このユーザー名を変更した後、アップグレードしてください。</span><span class="sxs-lookup"><span data-stu-id="c431c-105">Rename the user before you upgrade.</span></span> <span data-ttu-id="c431c-106">ユーザー名が変更されていないと、データベースはアップグレード処理後に問題ありの状態となり、データベースをオンラインにするまで使用できません。</span><span class="sxs-lookup"><span data-stu-id="c431c-106">If the user is not renamed, the database will be in a suspect state after the upgrade process and will be unavailable until the database is brought online.</span></span>  
  
## <a name="component"></a><span data-ttu-id="c431c-107">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="c431c-107">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="c431c-108">説明</span><span class="sxs-lookup"><span data-stu-id="c431c-108">Description</span></span>  
 <span data-ttu-id="c431c-109">ユーザー **sys**は予約されています。</span><span class="sxs-lookup"><span data-stu-id="c431c-109">User **sys** is reserved.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="c431c-110">修正措置</span><span class="sxs-lookup"><span data-stu-id="c431c-110">Corrective Action</span></span>  
  
### <a name="before-upgrade-procedure"></a><span data-ttu-id="c431c-111">アップグレード前に行う手順</span><span class="sxs-lookup"><span data-stu-id="c431c-111">Before Upgrade Procedure</span></span>  
 <span data-ttu-id="c431c-112">をアップグレードする前に、ユーザー **sys**を含む各データベースで、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="c431c-112">Before you upgrade, in each database that contains user **sys**, do the following:</span></span>  
  
1.  <span data-ttu-id="c431c-113">新しいユーザーを作成します。</span><span class="sxs-lookup"><span data-stu-id="c431c-113">Create a new user.</span></span>  
  
2.  <span data-ttu-id="c431c-114">次のステートメントを使用して、ユーザー **sys**によって付与され、ユーザー **sys**に付与されるすべてのアクセス許可を表示します。</span><span class="sxs-lookup"><span data-stu-id="c431c-114">Use the following statements to display all permissions that are granted by user **sys** and granted to user **sys**.</span></span>  
  
    ```  
    -- Return permissions granted by user sys.  
    SELECT * FROM sysprotects WHERE grantor = USER_ID('sys')  
    -- Return permissions granted to user sys.  
    SELECT * FROM sysprotects WHERE uid = USER_ID('sys')  
    ```  
  
3.  <span data-ttu-id="c431c-115">**Sys**が所有するすべてのオブジェクトの所有権を新しいユーザーに転送するには、 **sp_changeobjectowner**を使用します。</span><span class="sxs-lookup"><span data-stu-id="c431c-115">To transfer ownership of all objects owned by **sys** to the new user, use **sp_changeobjectowner**.</span></span>  
  
4.  <span data-ttu-id="c431c-116">ユーザー **sys**を削除します。</span><span class="sxs-lookup"><span data-stu-id="c431c-116">Drop user **sys**.</span></span>  
  
5.  <span data-ttu-id="c431c-117">手順 2. でキャプチャした元のアクセス許可を復元するには、GRANT ステートメントの AS *new_user*句を使用します。</span><span class="sxs-lookup"><span data-stu-id="c431c-117">To restore the original permissions captured in step 2, use the AS *new_user* clause of the GRANT statement.</span></span>  
  
6.  <span data-ttu-id="c431c-118">新しいユーザーを参照するようにスクリプトを修正します。</span><span class="sxs-lookup"><span data-stu-id="c431c-118">Modify scripts to reference the new user.</span></span> <span data-ttu-id="c431c-119">たとえば、`SELECT * FROM sys.my`_`table` などのステートメントを含むスクリプトを `SELECT * FROM new_user.my_table` に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c431c-119">For example, scripts that contain statements such as `SELECT * FROM sys.my`_`table` must be changed to `SELECT * FROM new_user.my_table`.</span></span>  
  
### <a name="after-upgrade-procedure"></a><span data-ttu-id="c431c-120">アップグレード後に行う手順</span><span class="sxs-lookup"><span data-stu-id="c431c-120">After Upgrade Procedure</span></span>  
 <span data-ttu-id="c431c-121">アップグレードの前にユーザー **sys**の名前を変更しなかった場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="c431c-121">If the user **sys** was not renamed prior to upgrading, do the following:</span></span>  
  
1.  <span data-ttu-id="c431c-122">ステートメント `ALTER DATABASE db_name SET ONLINE` を実行します。</span><span class="sxs-lookup"><span data-stu-id="c431c-122">Execute the statement `ALTER DATABASE db_name SET ONLINE`.</span></span> <span data-ttu-id="c431c-123">データベースが SINGLE_USER モードになります。</span><span class="sxs-lookup"><span data-stu-id="c431c-123">The database will be in SINGLE_USER mode.</span></span>  
  
2.  <span data-ttu-id="c431c-124">「アップグレード前に行う手順」セクションのすべての手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="c431c-124">Follow all steps in the Before Upgrade Procedure section.</span></span>  
  
3.  <span data-ttu-id="c431c-125">ステートメント `ALTER DATABASE db_name SET MULTI_USER` を実行します。</span><span class="sxs-lookup"><span data-stu-id="c431c-125">Execute the statement `ALTER DATABASE db_name SET MULTI_USER`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c431c-126">参照</span><span class="sxs-lookup"><span data-stu-id="c431c-126">See Also</span></span>  
 <span data-ttu-id="c431c-127">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="c431c-127">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="c431c-128">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="c431c-128">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  

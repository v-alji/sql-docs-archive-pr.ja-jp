---
title: cross db ownership chaining サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- cross-database ownership chaining
- cross db ownership chaining option
- chaining ownership
ms.assetid: 7b2d49f2-b91c-4aee-a52b-6cc49bed03af
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cfb768065cc0aa2aaa7aed0f996b18e46f1da7ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641865"
---
# <a name="cross-db-ownership-chaining-server-configuration-option"></a><span data-ttu-id="ecb05-102">cross db ownership chaining サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="ecb05-102">cross db ownership chaining Server Configuration Option</span></span>
  <span data-ttu-id="ecb05-103">**cross db ownership chaining** オプションは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに対して、複数データベースの組み合わせ所有権を構成するために使用します。</span><span class="sxs-lookup"><span data-stu-id="ecb05-103">Use the **cross db ownership chaining** option to configure cross-database ownership chaining for an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="ecb05-104">このサーバー オプションを使用すると、次に示すように、データベース レベルで複数データベースの組み合わせ所有権を制御したり、すべてのデータベースに複数データベースの組み合わせ所有権を許可できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ecb05-104">This server option allows you to control cross-database ownership chaining at the database level or to allow cross-database ownership chaining for all databases:</span></span>  
  
-   <span data-ttu-id="ecb05-105">インスタンスの **cross db ownership chaining** がオフ (0) になっていると、複数データベースの組み合わせ所有権はすべてのデータベースで無効になります。</span><span class="sxs-lookup"><span data-stu-id="ecb05-105">When **cross db ownership chaining** is off (0) for the instance, cross-database ownership chaining is disabled for all databases.</span></span>  
  
-   <span data-ttu-id="ecb05-106">インスタンスの **cross db ownership chaining** がオン (1) になっていると、複数データベースの組み合わせ所有権はすべてのデータベースで有効になります。</span><span class="sxs-lookup"><span data-stu-id="ecb05-106">When **cross db ownership chaining** is on (1) for the instance, cross-database ownership chaining is on for all databases.</span></span>  
  
-   <span data-ttu-id="ecb05-107">ALTER DATABASE ステートメントの SET 句を使用すると、個別のデータベースに複数データベースの組み合わせ所有権を設定できます。</span><span class="sxs-lookup"><span data-stu-id="ecb05-107">You can set cross-database ownership chaining for individual databases using the SET clause of the ALTER DATABASE statement.</span></span> <span data-ttu-id="ecb05-108">新しいデータベースを作成する場合、CREATE DATABASE ステートメントを使用すると、新しいデータベースに複数データベースの組み合わせ所有権オプションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="ecb05-108">If you are creating a new database, you can set the cross-database ownership chaining option for the new database using the CREATE DATABASE statement.</span></span>  
  
     <span data-ttu-id="ecb05-109">**cross db ownership chaining** を 1 に設定することはお勧めしません。この設定を行う場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスによってホストされているすべてのデータベースが複数データベースの組み合わせ所有権に参加する必要があります。また、この設定がセキュリティに与える影響も理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="ecb05-109">Setting **cross db ownership chaining** to 1 is not recommended unless all of the databases hosted by the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must participate in cross-database ownership chaining and you are aware of the security implications of this setting.</span></span>  
  
## <a name="controlling-cross-database-ownership-chaining"></a><span data-ttu-id="ecb05-110">複数データベースの組み合わせ所有権の制御</span><span class="sxs-lookup"><span data-stu-id="ecb05-110">Controlling Cross-Database Ownership Chaining</span></span>  
 <span data-ttu-id="ecb05-111">複数データベースの組み合わせ所有権のオンとオフを切り替える前に、次の項目について検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ecb05-111">Before turning cross-database ownership chaining on or off, consider the following:</span></span>  
  
-   <span data-ttu-id="ecb05-112">複数データベースの組み合わせ所有権のオンとオフを切り替えるには、 **sysadmin** 固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="ecb05-112">You must be a member of the **sysadmin** fixed server role to turn cross-database ownership chaining on or off.</span></span>  
  
-   <span data-ttu-id="ecb05-113">実稼動サーバーで複数データベースの組み合わせ所有権をオフにするには、サード パーティのアプリケーションを含むすべてのアプリケーションを十分にテストし、この変更がアプリケーションの機能に影響を与えないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="ecb05-113">Before turning off cross-database ownership chaining on a production server, fully test all applications, including third-party applications, to ensure that the changes do not affect application functionality.</span></span>  
  
-   <span data-ttu-id="ecb05-114">**sp_configure** で RECONFIGURE を指定すると、サーバーの実行中に **cross db ownership chaining**オプションを変更できます。</span><span class="sxs-lookup"><span data-stu-id="ecb05-114">You can change the **cross db ownership chaining** option while the server is running if you specify RECONFIGURE with **sp_configure**.</span></span>  
  
-   <span data-ttu-id="ecb05-115">複数データベースの組み合わせ所有権が必要なデータベースがある場合、推奨される操作としては、まず **sp_configure** を使用してインスタンスの **cross db ownership chaining**オプションをオフにします。次に、ALTER DATABASE ステートメントを使用し、個別のデータベースの複数データベースの組み合わせ所有権をオンにします。</span><span class="sxs-lookup"><span data-stu-id="ecb05-115">If you have databases that require cross-database ownership chaining, the recommended practice is to turn off the **cross db ownership chaining** option for the instance using **sp_configure**; then turn on cross-database ownership chaining for individual databases that require it using the ALTER DATABASE statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecb05-116">参照</span><span class="sxs-lookup"><span data-stu-id="ecb05-116">See Also</span></span>  
 <span data-ttu-id="ecb05-117">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ecb05-117">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="ecb05-118">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ecb05-118">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 <span data-ttu-id="ecb05-119">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ecb05-119">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="ecb05-120">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ecb05-120">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="ecb05-121">RECONFIGURE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ecb05-121">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  

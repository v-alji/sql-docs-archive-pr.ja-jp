---
title: contained database authentication サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- contained_database_authentication_TSQL
- contained database authentication
helpviewer_keywords:
- contained database, enabling
- contained database authentication option
ms.assetid: b80768d2-ac20-4035-a335-d9adb74b3f6e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cf5bf07c8b0913ff81f31ff0ca64a18eee0f2ac2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642285"
---
# <a name="contained-database-authentication-server-configuration-option"></a><span data-ttu-id="698d8-102">contained database authentication サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="698d8-102">contained database authentication Server Configuration Option</span></span>
  <span data-ttu-id="698d8-103">**contained database authentication** オプションを使用して、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンス上で包含データベースを有効にします。</span><span class="sxs-lookup"><span data-stu-id="698d8-103">Use the **contained database authentication** option to enable contained databases on the instance of [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
 <span data-ttu-id="698d8-104">このサーバー オプションでは、 **contained database authentication**を制御できます。</span><span class="sxs-lookup"><span data-stu-id="698d8-104">This server option allows you to control **contained database authentication**.</span></span>  
  
-   <span data-ttu-id="698d8-105">インスタンスで **contained database authentication** がオフ (0) の場合、包含データベースを作成したり [!INCLUDE[ssDE](../../includes/ssde-md.md)]にアタッチしたりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="698d8-105">When **contained database authentication** is off (0) for the instance, contained databases cannot be created, or attached to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="698d8-106">インスタンスで **contained database authentication** がオン (1) の場合、包含データベースを作成したり [!INCLUDE[ssDE](../../includes/ssde-md.md)]にアタッチしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="698d8-106">When **contained database authentication** is on (1) for the instance, contained databases can be created, or attached to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="698d8-107">包含データベースには、すべてのデータベース設定と、データベースを定義するために必要なメタデータが含まれており、データベースがインストールされている [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに対する構成上の依存関係がありません。</span><span class="sxs-lookup"><span data-stu-id="698d8-107">A contained database includes all database settings and metadata required to define the database and has no configuration dependencies on the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] where the database is installed.</span></span> <span data-ttu-id="698d8-108">ユーザーは、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] レベルでのログイン認証なしで包含データベースに接続できます。</span><span class="sxs-lookup"><span data-stu-id="698d8-108">Users can connect to the database without authenticating a login at the [!INCLUDE[ssDE](../../includes/ssde-md.md)] level.</span></span> <span data-ttu-id="698d8-109">データベース エンジンからデータベースを分離すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の他のインスタンスにデータベースを簡単に移動できるようになります。</span><span class="sxs-lookup"><span data-stu-id="698d8-109">Isolating the database from the Database Engine makes it possible to easily move the database to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="698d8-110">すべてのデータベース設定をデータベースに含めることによって、データベース所有者はデータベースのすべての構成設定を管理できるようになります。</span><span class="sxs-lookup"><span data-stu-id="698d8-110">Including all the database settings in the database enables database owners to manage all the configuration settings for the database.</span></span> <span data-ttu-id="698d8-111">包含データベースの詳細については、「 [Contained Databases](../../relational-databases/databases/contained-databases.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="698d8-111">For more information about contained databases, see [Contained Databases](../../relational-databases/databases/contained-databases.md).</span></span>  
  
 <span data-ttu-id="698d8-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに包含データベースが存在する場合、**contained database authentication** の設定は **RECONFIGURE WITH OVERRIDE** ステートメントを使用して 0 に設定できます。</span><span class="sxs-lookup"><span data-stu-id="698d8-112">If an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has any contained databases the **contained database authentication** setting can be set to 0 by using the **RECONFIGURE WITH OVERRIDE** statement.</span></span> <span data-ttu-id="698d8-113">**contained database authentication** を 0 に設定すると、包含データベースに対して contained database authentication が無効になります。</span><span class="sxs-lookup"><span data-stu-id="698d8-113">Setting **contained database authentication** to 0 will disable contained database authentication for the contained databases.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="698d8-114">包含データベースを有効にすると、ALTER ANY USER 権限を持つデータベース ユーザー (db_owner ロールおよび db_accessadmin データベース ロールのメンバーなど) は、データベースへのアクセスが許可されます。そうすることで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへのアクセスが許可されます。</span><span class="sxs-lookup"><span data-stu-id="698d8-114">When contained databases are enabled, database users with the ALTER ANY USER permission, such as members of the db_owner and db_accessadmin database roles, can grant access to databases and by doing so, grant access to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="698d8-115">これは、サーバーへのアクセスの制御は sysadmin および securityadmin 固定サーバー ロールのメンバー、およびサーバー レベルでの管理 CONTROL SERVER および ALTER ANY LOGIN 権限によるログインに制限されなくなることを意味します。</span><span class="sxs-lookup"><span data-stu-id="698d8-115">This means that control over access to the server is no longer limited to members of the sysadmin and securityadmin fixed server role, and logins with the server level CONTROL SERVER and ALTER ANY LOGIN permission.</span></span> <span data-ttu-id="698d8-116">包含データベースを許可する前に、包含データベースに関連するリスクを理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="698d8-116">Before allowing contained databases, you should understand the risks associated with contained databases.</span></span> <span data-ttu-id="698d8-117">詳細については、「 [Security Best Practices with Contained Databases](../../relational-databases/databases/security-best-practices-with-contained-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="698d8-117">For more information, see [Security Best Practices with Contained Databases](../../relational-databases/databases/security-best-practices-with-contained-databases.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="698d8-118">例</span><span class="sxs-lookup"><span data-stu-id="698d8-118">Examples</span></span>  
 <span data-ttu-id="698d8-119">次の例では、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスで包含データベースを有効にします。</span><span class="sxs-lookup"><span data-stu-id="698d8-119">The following example enables contained databases on the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
```sql  
sp_configure 'contained database authentication', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="698d8-120">参照</span><span class="sxs-lookup"><span data-stu-id="698d8-120">See Also</span></span>  
 <span data-ttu-id="698d8-121">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="698d8-121">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="698d8-122">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="698d8-122">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 [<span data-ttu-id="698d8-123">サーバー構成オプション &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="698d8-123">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  

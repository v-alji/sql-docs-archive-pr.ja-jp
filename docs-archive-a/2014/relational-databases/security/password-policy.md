---
title: パスワード ポリシー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- ALTER LOGIN statement
- passwords [SQL Server], policy enforcement
- logins [SQL Server], passwords
- CHECK_EXPIRATION option
- complex passwords [SQL Server]
- passwords [SQL Server], expiration
- manual bad password count resets
- MUST_CHANGE option
- expiration [SQL Server]
- expired password [SQL Server]
- symbols [SQL Server]
- NetValidatePasswordPolicy() API
- passwords [SQL Server]
- password policy [SQL Server]
- resetting bad password counts
- security [SQL Server], passwords
- CHECK_POLICY option
- passwords [SQL Server], symbols
- bad password counts
- passwords [SQL Server], complexity
- characters [SQL Server], password policies
ms.assetid: c0040c0a-a18f-45b9-9c40-0625685649b1
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 902c46b4609a32139450843414a3c4d97b52fcf7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633016"
---
# <a name="password-policy"></a><span data-ttu-id="c7c33-102">パスワード ポリシー</span><span class="sxs-lookup"><span data-stu-id="c7c33-102">Password Policy</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c7c33-103">Windows のパスワード ポリシー メカニズムに対応しています。</span><span class="sxs-lookup"><span data-stu-id="c7c33-103">can use Windows password policy mechanisms.</span></span> <span data-ttu-id="c7c33-104">パスワード ポリシーは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用するログインに適用され、パスワードを持つ包含データベース ユーザーに適用されます。</span><span class="sxs-lookup"><span data-stu-id="c7c33-104">The password policy applies to a login that uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentication, and to a contained database user with password.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="c7c33-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]内部で使用されるパスワードに、Windows で使用されているものと同じ複雑性ポリシーおよび有効期限ポリシーを適用できます。</span><span class="sxs-lookup"><span data-stu-id="c7c33-105">can apply the same complexity and expiration policies used in Windows to passwords used inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c7c33-106">この機能は `NetValidatePasswordPolicy` API に依存します。</span><span class="sxs-lookup"><span data-stu-id="c7c33-106">This functionality depends on the `NetValidatePasswordPolicy` API.</span></span>  
  
## <a name="password-complexity"></a><span data-ttu-id="c7c33-107">パスワードの複雑性</span><span class="sxs-lookup"><span data-stu-id="c7c33-107">Password Complexity</span></span>  
 <span data-ttu-id="c7c33-108">パスワードの複雑性のポリシーは、使用可能なパスワードの数を増やすことにより、総当り攻撃を防ぐようにデザインされています。</span><span class="sxs-lookup"><span data-stu-id="c7c33-108">Password complexity policies are designed to deter brute force attacks by increasing the number of possible passwords.</span></span> <span data-ttu-id="c7c33-109">パスワードの複雑性のポリシーが適用される場合、新しいパスワードは次のガイドラインを満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7c33-109">When password complexity policy is enforced, new passwords must meet the following guidelines:</span></span>  
  
-   <span data-ttu-id="c7c33-110">パスワードはユーザー アカウント名を含まない。</span><span class="sxs-lookup"><span data-stu-id="c7c33-110">The password does not contain the account name of the user.</span></span>  
  
-   <span data-ttu-id="c7c33-111">パスワードは 8 文字以上である。</span><span class="sxs-lookup"><span data-stu-id="c7c33-111">The password is at least eight characters long.</span></span>  
  
-   <span data-ttu-id="c7c33-112">パスワードは次の 4 つのカテゴリのうちの 3 つのカテゴリの文字を含む。</span><span class="sxs-lookup"><span data-stu-id="c7c33-112">The password contains characters from three of the following four categories:</span></span>  
  
    -   <span data-ttu-id="c7c33-113">ラテン文字の大文字 (A ～ Z)</span><span class="sxs-lookup"><span data-stu-id="c7c33-113">Latin uppercase letters (A through Z)</span></span>  
  
    -   <span data-ttu-id="c7c33-114">ラテン文字の小文字 (a ～ z)</span><span class="sxs-lookup"><span data-stu-id="c7c33-114">Latin lowercase letters (a through z)</span></span>  
  
    -   <span data-ttu-id="c7c33-115">算用数字 (0 ～ 9)</span><span class="sxs-lookup"><span data-stu-id="c7c33-115">Base 10 digits (0 through 9)</span></span>  
  
    -   <span data-ttu-id="c7c33-116">感嘆符 (!)、ドル記号 ($)、番号記号 (#)、パーセント記号 (%) などの英数字以外の文字</span><span class="sxs-lookup"><span data-stu-id="c7c33-116">Non-alphanumeric characters such as: exclamation point (!), dollar sign ($), number sign (#), or percent (%).</span></span>  
  
 <span data-ttu-id="c7c33-117">パスワードには最大 128 文字まで使用できます。</span><span class="sxs-lookup"><span data-stu-id="c7c33-117">Passwords can be up to 128 characters long.</span></span> <span data-ttu-id="c7c33-118">パスワードはできるだけ長く、複雑にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c7c33-118">You should use passwords that are as long and complex as possible.</span></span>  
  
## <a name="password-expiration"></a><span data-ttu-id="c7c33-119">パスワードの有効期限</span><span class="sxs-lookup"><span data-stu-id="c7c33-119">Password Expiration</span></span>  
 <span data-ttu-id="c7c33-120">パスワードの有効期限のポリシーは、パスワードの寿命を管理します。</span><span class="sxs-lookup"><span data-stu-id="c7c33-120">Password expiration policies are used to manage the lifespan of a password.</span></span> <span data-ttu-id="c7c33-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってパスワードの有効期限が適用されている場合、ユーザーは古いパスワードを変更するよう通知され、有効期限が切れたパスワードを持つアカウントは無効になります。</span><span class="sxs-lookup"><span data-stu-id="c7c33-121">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enforces password expiration policy, users are reminded to change old passwords, and accounts that have expired passwords are disabled.</span></span>  
  
## <a name="policy-enforcement"></a><span data-ttu-id="c7c33-122">ポリシーの適用</span><span class="sxs-lookup"><span data-stu-id="c7c33-122">Policy Enforcement</span></span>  
 <span data-ttu-id="c7c33-123">パスワード ポリシーの適用は、SQL Server ログインごとに個別に構成できます。</span><span class="sxs-lookup"><span data-stu-id="c7c33-123">The enforcement of password policy can be configured separately for each SQL Server login.</span></span> <span data-ttu-id="c7c33-124">[ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) を使用して、SQL Server ログインのパスワード ポリシー オプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="c7c33-124">Use [ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) to configure the password policy options of a SQL Server login.</span></span> <span data-ttu-id="c7c33-125">パスワード ポリシーの適用を構成する際に、次の規則が当てはまります。</span><span class="sxs-lookup"><span data-stu-id="c7c33-125">The following rules apply to the configuration of password policy enforcement:</span></span>  
  
-   <span data-ttu-id="c7c33-126">CHECK_POLICY を ON に変更した場合、次の動作が行われます。</span><span class="sxs-lookup"><span data-stu-id="c7c33-126">When CHECK_POLICY is changed to ON, the following behaviors occur:</span></span>  
  
    -   <span data-ttu-id="c7c33-127">CHECK_EXPIRATION も、明示的に OFF に設定されない限り、ON に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c7c33-127">CHECK_EXPIRATION is also set to ON unless it is explicitly set to OFF.</span></span>  
  
    -   <span data-ttu-id="c7c33-128">パスワードの履歴が、現在のパスワード ハッシュの値に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="c7c33-128">The password history is initialized with the value of the current password hash.</span></span>  
  
    -   <span data-ttu-id="c7c33-129">**[アカウント ロックアウトの期間]** 、 **[アカウント ロックアウトのしきい値]** 、および **[ロックアウト カウンターのリセット]** も有効になります。</span><span class="sxs-lookup"><span data-stu-id="c7c33-129">**Account lockout duration**, **account lockout threshold**, and **reset account lockout counter after** are also enabled.</span></span>  
  
-   <span data-ttu-id="c7c33-130">CHECK_POLICY を OFF に変更した場合、次の動作が行われます。</span><span class="sxs-lookup"><span data-stu-id="c7c33-130">When CHECK_POLICY is changed to OFF, the following behaviors occur:</span></span>  
  
    -   <span data-ttu-id="c7c33-131">CHECK_EXPIRATION も OFF に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c7c33-131">CHECK_EXPIRATION is also set to OFF.</span></span>  
  
    -   <span data-ttu-id="c7c33-132">パスワード履歴は消去されます。</span><span class="sxs-lookup"><span data-stu-id="c7c33-132">The password history is cleared.</span></span>  
  
    -   <span data-ttu-id="c7c33-133">`lockout_time` の値がリセットされます。</span><span class="sxs-lookup"><span data-stu-id="c7c33-133">The value of `lockout_time` is reset.</span></span>  
  
 <span data-ttu-id="c7c33-134">ポリシー オプションの組み合わせには、サポートされないものがあります。</span><span class="sxs-lookup"><span data-stu-id="c7c33-134">Some combinations of policy options are not supported.</span></span>  
  
-   <span data-ttu-id="c7c33-135">MUST_CHANGE が指定された場合、CHECK_EXPIRATION および CHECK_POLICY は ON に設定されなければなりません。</span><span class="sxs-lookup"><span data-stu-id="c7c33-135">If MUST_CHANGE is specified, CHECK_EXPIRATION and CHECK_POLICY must be set to ON.</span></span> <span data-ttu-id="c7c33-136">ON に設定しない場合、ステートメントは失敗します。</span><span class="sxs-lookup"><span data-stu-id="c7c33-136">Otherwise, the statement will fail.</span></span>  
  
-   <span data-ttu-id="c7c33-137">CHECK_POLICY を OFF に設定した場合、CHECK_EXPIRATION を ON に設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="c7c33-137">If CHECK_POLICY is set to OFF, CHECK_EXPIRATION cannot be set to ON.</span></span> <span data-ttu-id="c7c33-138">このオプションの組み合わせで ALTER LOGIN ステートメントを実行すると、ステートメントは失敗します。</span><span class="sxs-lookup"><span data-stu-id="c7c33-138">An ALTER LOGIN statement that has this combination of options will fail.</span></span>  
  
 <span data-ttu-id="c7c33-139">CHECK_POLICY = ON を設定すると、次のようなパスワードは作成できなくなります。</span><span class="sxs-lookup"><span data-stu-id="c7c33-139">Setting CHECK_POLICY = ON will prevent the creation of passwords that are:</span></span>  
  
-   <span data-ttu-id="c7c33-140">NULL または空文字列</span><span class="sxs-lookup"><span data-stu-id="c7c33-140">Null or empty</span></span>  
  
-   <span data-ttu-id="c7c33-141">コンピューター名またはログイン名と同じ文字列</span><span class="sxs-lookup"><span data-stu-id="c7c33-141">Same as name of computer or login</span></span>  
  
-   <span data-ttu-id="c7c33-142">"password"、"admin"、"administrator"、"sa"、"sysadmin" のいずれかの文字列</span><span class="sxs-lookup"><span data-stu-id="c7c33-142">Any of the following: "password", "admin", "administrator", "sa", "sysadmin"</span></span>  
  
 <span data-ttu-id="c7c33-143">セキュリティ ポリシーは、Windows で設定する場合も、ドメインから受け取る場合もあります。</span><span class="sxs-lookup"><span data-stu-id="c7c33-143">The security policy might be set in Windows, or might be received from the domain.</span></span> <span data-ttu-id="c7c33-144">コンピューターでパスワード ポリシーを表示するには、ローカル セキュリティ ポリシーの MMC スナップイン (**secpol.msc**) を使用します。</span><span class="sxs-lookup"><span data-stu-id="c7c33-144">To view the password policy on the computer, use the Local Security Policy MMC snap-in (**secpol.msc**).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="c7c33-145">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="c7c33-145">Related Tasks</span></span>  
 [<span data-ttu-id="c7c33-146">CREATE LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c7c33-146">CREATE LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-login-transact-sql)  
  
 [<span data-ttu-id="c7c33-147">ALTER LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c7c33-147">ALTER LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-login-transact-sql)  
  
 [<span data-ttu-id="c7c33-148">CREATE USER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c7c33-148">CREATE USER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-user-transact-sql)  
  
 [<span data-ttu-id="c7c33-149">ALTER USER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c7c33-149">ALTER USER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-user-transact-sql)  
  
 [<span data-ttu-id="c7c33-150">ログインの作成</span><span class="sxs-lookup"><span data-stu-id="c7c33-150">Create a Login</span></span>](authentication-access/create-a-login.md)  
  
 [<span data-ttu-id="c7c33-151">データベース ユーザーの作成</span><span class="sxs-lookup"><span data-stu-id="c7c33-151">Create a Database User</span></span>](authentication-access/create-a-database-user.md)  
  
## <a name="related-content"></a><span data-ttu-id="c7c33-152">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="c7c33-152">Related Content</span></span>  
 [<span data-ttu-id="c7c33-153">強力なパスワード</span><span class="sxs-lookup"><span data-stu-id="c7c33-153">Strong Passwords</span></span>](strong-passwords.md)  
  
  

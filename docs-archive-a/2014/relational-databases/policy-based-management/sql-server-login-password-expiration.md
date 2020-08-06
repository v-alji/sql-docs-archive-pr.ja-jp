---
title: SQL Server ログイン パスワードの有効期限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 7e3bf9da-a436-433d-847a-47c30428cad3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 678e8e9c6b567014bdd49e89d043165bc48d168a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631846"
---
# <a name="sql-server-login-password-expiration"></a><span data-ttu-id="5f368-102">SQL Server ログイン パスワードの有効期限</span><span class="sxs-lookup"><span data-stu-id="5f368-102">SQL Server Login Password Expiration</span></span>
  <span data-ttu-id="5f368-103">このルールでは、各 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインの "パスワードの有効期限" が有効になっているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="5f368-103">This rule checks whether "Password expiration" of each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login is enabled.</span></span> <span data-ttu-id="5f368-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証が有効で、オペレーティング システムが [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]よりも前のバージョンである場合、攻撃者は既知の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン パスワードを繰り返し利用できます。</span><span class="sxs-lookup"><span data-stu-id="5f368-104">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication is enabled and if the operating system version is earlier than [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)], an attacker could repeatedly exploit a known [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login password.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="5f368-105">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="5f368-105">Best Practices Recommendations</span></span>  
 <span data-ttu-id="5f368-106">オペレーティング システムを [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]にアップグレードすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5f368-106">We recommend that you upgrade the operating system to [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)].</span></span>  
  
 <span data-ttu-id="5f368-107">使用している環境で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証が必要ではない場合は、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="5f368-107">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication is not required in your environment, use Windows Authentication.</span></span> <span data-ttu-id="5f368-108">詳細については、「 [認証モードの選択](../security/choose-an-authentication-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f368-108">For more information, see [Choose an Authentication Mode](../security/choose-an-authentication-mode.md).</span></span>  
  
 <span data-ttu-id="5f368-109">すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインに対して、"パスワードの有効期限" を有効にします。</span><span class="sxs-lookup"><span data-stu-id="5f368-109">Enable "Password expiration" for all the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span> <span data-ttu-id="5f368-110">[ログインのパスワード ポリシーを構成するには、](/sql/t-sql/statements/alter-login-transact-sql) ALTER LOGIN [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用します。</span><span class="sxs-lookup"><span data-stu-id="5f368-110">Use [ALTER LOGIN](/sql/t-sql/statements/alter-login-transact-sql) to configure the password policy for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="5f368-111">詳細情報</span><span class="sxs-lookup"><span data-stu-id="5f368-111">For More Information</span></span>  
 [<span data-ttu-id="5f368-112">パスワード ポリシー</span><span class="sxs-lookup"><span data-stu-id="5f368-112">Password Policy</span></span>](../security/password-policy.md)  
  
## <a name="see-also"></a><span data-ttu-id="5f368-113">参照</span><span class="sxs-lookup"><span data-stu-id="5f368-113">See Also</span></span>  
 [<span data-ttu-id="5f368-114">ポリシーベースの管理を使用したベスト プラクティスの監視と実行</span><span class="sxs-lookup"><span data-stu-id="5f368-114">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  

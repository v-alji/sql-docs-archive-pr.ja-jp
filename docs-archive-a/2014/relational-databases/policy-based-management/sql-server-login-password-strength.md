---
title: SQL Server ログイン パスワードの強度 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: b0862c3a-926b-490c-a37f-382e50146a3e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5534748fbbf810539f2dcfc22239e4b987cf0f77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713037"
---
# <a name="sql-server-login-password-strength"></a><span data-ttu-id="67d8e-102">SQL Server ログイン パスワードの強度</span><span class="sxs-lookup"><span data-stu-id="67d8e-102">SQL Server Login Password Strength</span></span>
  <span data-ttu-id="67d8e-103">このルールでは、各 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインの [パスワード ポリシーを適用する] が有効になっているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="67d8e-103">This rule checks whether "Enforce password policy" of each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login is enabled.</span></span> <span data-ttu-id="67d8e-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証が有効で、オペレーティング システムが [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]よりも前のバージョンである場合、攻撃者は既知の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン パスワードを繰り返し利用できます。</span><span class="sxs-lookup"><span data-stu-id="67d8e-104">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication is enabled and if the operating system version is earlier than [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)], an attacker could repeatedly exploit a known [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login password.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="67d8e-105">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="67d8e-105">Best Practices Recommendations</span></span>  
 <span data-ttu-id="67d8e-106">オペレーティング システムを [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]にアップグレードすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="67d8e-106">We recommend that you upgrade the operating system to [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)].</span></span>  
  
 <span data-ttu-id="67d8e-107">使用している環境で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証が必要ではない場合は、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="67d8e-107">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication is not required in your environment, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="67d8e-108">すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインに対して、[パスワード ポリシーを適用する] を有効にします。</span><span class="sxs-lookup"><span data-stu-id="67d8e-108">Enable "Enforce password policy" for all the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span> <span data-ttu-id="67d8e-109">[ログインのパスワード ポリシーを構成するには、](/sql/t-sql/statements/alter-login-transact-sql) ALTER LOGIN [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用します。</span><span class="sxs-lookup"><span data-stu-id="67d8e-109">Use [ALTER LOGIN](/sql/t-sql/statements/alter-login-transact-sql) to configure the password policy for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="67d8e-110">詳細情報</span><span class="sxs-lookup"><span data-stu-id="67d8e-110">For More Information</span></span>  
 [<span data-ttu-id="67d8e-111">パスワード ポリシー</span><span class="sxs-lookup"><span data-stu-id="67d8e-111">Password Policy</span></span>](../security/password-policy.md)  
  
## <a name="see-also"></a><span data-ttu-id="67d8e-112">参照</span><span class="sxs-lookup"><span data-stu-id="67d8e-112">See Also</span></span>  
 [<span data-ttu-id="67d8e-113">ポリシーベースの管理を使用したベスト プラクティスの監視と実行</span><span class="sxs-lookup"><span data-stu-id="67d8e-113">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  

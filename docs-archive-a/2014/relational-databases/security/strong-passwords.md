---
title: 強力なパスワード | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server], passwords
- passwords [SQL Server], strong
- symbols [SQL Server]
- security [SQL Server], passwords
- passwords [SQL Server], symbols
- characters [SQL Server], password policies
- strong passwords [SQL Server]
ms.assetid: 338548f4-c4d8-47ca-b597-5c9c0f2fa205
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 5e878e0de5ee1f496dcc981182d42f5898838c64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713985"
---
# <a name="strong-passwords"></a><span data-ttu-id="2341e-102">強力なパスワード</span><span class="sxs-lookup"><span data-stu-id="2341e-102">Strong Passwords</span></span>
  <span data-ttu-id="2341e-103">パスワードは、サーバーのセキュリティ上で最も弱点になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2341e-103">Passwords can be the weakest link in a server security deployment.</span></span> <span data-ttu-id="2341e-104">パスワードを選択するときは、常に最大限の注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="2341e-104">You should always take great care when you select a password.</span></span> <span data-ttu-id="2341e-105">強力なパスワードの特徴は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2341e-105">A strong password has the following characteristics:</span></span>  
  
-   <span data-ttu-id="2341e-106">8 文字以上である</span><span class="sxs-lookup"><span data-stu-id="2341e-106">Is at least 8 characters long.</span></span>  
  
-   <span data-ttu-id="2341e-107">文字、数字、および記号を組み合わせたパスワードである</span><span class="sxs-lookup"><span data-stu-id="2341e-107">Combines letters, numbers, and symbol characters within the password.</span></span>  
  
-   <span data-ttu-id="2341e-108">辞書に載っていない</span><span class="sxs-lookup"><span data-stu-id="2341e-108">Is not found in a dictionary.</span></span>  
  
-   <span data-ttu-id="2341e-109">コマンド名ではない</span><span class="sxs-lookup"><span data-stu-id="2341e-109">Is not the name of a command.</span></span>  
  
-   <span data-ttu-id="2341e-110">人名ではない</span><span class="sxs-lookup"><span data-stu-id="2341e-110">Is not the name of a person.</span></span>  
  
-   <span data-ttu-id="2341e-111">ユーザー名ではない</span><span class="sxs-lookup"><span data-stu-id="2341e-111">Is not the name of a user.</span></span>  
  
-   <span data-ttu-id="2341e-112">コンピューター名ではない</span><span class="sxs-lookup"><span data-stu-id="2341e-112">Is not the name of a computer.</span></span>  
  
-   <span data-ttu-id="2341e-113">定期的に変更される</span><span class="sxs-lookup"><span data-stu-id="2341e-113">Is changed regularly.</span></span>  
  
-   <span data-ttu-id="2341e-114">以前のパスワードと明らかに異なる</span><span class="sxs-lookup"><span data-stu-id="2341e-114">Is significantly different from previous passwords.</span></span>  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="2341e-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のパスワードは、最大 128 文字までで、英字、記号、数字を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2341e-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] passwords can contain up to 128 characters, including letters, symbols, and digits.</span></span> <span data-ttu-id="2341e-116">ログイン、ユーザー名、ロール、およびパスワードは [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで使用されることが多く、特定の記号については二重引用符 (") または角かっこ ([ ]) で囲む必要が生じます。</span><span class="sxs-lookup"><span data-stu-id="2341e-116">Because logins, user names, roles, and passwords are frequently used in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, certain symbols must be enclosed by double quotation marks (") or square brackets ([ ]).</span></span> <span data-ttu-id="2341e-117">これらの区切り記号を [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで使用するのは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のログイン、ユーザー、ロール、またはパスワードに次のような特徴がある場合です。</span><span class="sxs-lookup"><span data-stu-id="2341e-117">Use these delimiters in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login, user, role, or password has the following characteristics:</span></span>  
  
-   <span data-ttu-id="2341e-118">スペースが含まれているか、スペースが先頭にある</span><span class="sxs-lookup"><span data-stu-id="2341e-118">Contains or starts with a space character.</span></span>  
  
-   <span data-ttu-id="2341e-119">$ または \@ で始まる</span><span class="sxs-lookup"><span data-stu-id="2341e-119">Starts with the $ or \@ character.</span></span>  
  
 <span data-ttu-id="2341e-120">OLE DB または ODBC の接続文字列で使用する場合、ログインまたはパスワードに次の文字は含めないでください: [] {}() , ; ?</span><span class="sxs-lookup"><span data-stu-id="2341e-120">If used in an OLE DB or ODBC connection string, a login or password must not contain the following characters: [] {}() , ; ?</span></span> <span data-ttu-id="2341e-121">\* !</span><span class="sxs-lookup"><span data-stu-id="2341e-121">\* !</span></span> <span data-ttu-id="2341e-122">\@.</span><span class="sxs-lookup"><span data-stu-id="2341e-122">\@.</span></span> <span data-ttu-id="2341e-123">これらの文字は、接続の初期化や、接続の値を区切る場合に使用されています。</span><span class="sxs-lookup"><span data-stu-id="2341e-123">These characters are used to either initialize a connection or separate connection values.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="2341e-124">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="2341e-124">Related Content</span></span>  
 [<span data-ttu-id="2341e-125">パスワード ポリシー</span><span class="sxs-lookup"><span data-stu-id="2341e-125">Password Policy</span></span>](password-policy.md)  
  
  

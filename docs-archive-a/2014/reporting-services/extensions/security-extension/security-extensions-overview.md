---
title: セキュリティ拡張機能の概要 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- security [Reporting Services], extensions
ms.assetid: 24ccd795-6506-457c-93ac-6a9dd6bb9a46
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9cd6c2a1518b724a7faafecdb2926505694e9707
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641472"
---
# <a name="security-extensions-overview"></a><span data-ttu-id="4877d-102">セキュリティ拡張機能の概要</span><span class="sxs-lookup"><span data-stu-id="4877d-102">Security Extensions Overview</span></span>
  <span data-ttu-id="4877d-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] セキュリティ拡張機能を使用すると、ユーザーまたはグループの認証と承認を行えます。つまり、複数のユーザーがレポート サーバーにログオンし、それぞれ異なるタスクや操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="4877d-103">A [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] security extension enables the authentication and authorization of users or groups; that is, it enables different users to log on to a report server and, based on their identities, perform different tasks or operations.</span></span> <span data-ttu-id="4877d-104">既定では、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] は Windows ベースの認証拡張機能を使用します。この拡張機能は Windows アカウント プロトコルを使用して、システムのアカウントを持っていると主張するユーザーの ID を検証します。</span><span class="sxs-lookup"><span data-stu-id="4877d-104">By default, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] uses a Windows-based authentication extension, which uses Windows account protocols to verify the identities of users who claim to have accounts on the system.</span></span> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="4877d-105">は、ロールベースのセキュリティ システムを使用してユーザーを承認します。</span><span class="sxs-lookup"><span data-stu-id="4877d-105">uses a role-based security system to authorize users.</span></span> <span data-ttu-id="4877d-106">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のロールベースのセキュリティ モデルは、他の技術に見られるロールベースのセキュリティ モデルと類似しています。</span><span class="sxs-lookup"><span data-stu-id="4877d-106">The [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] role-based security model is similar to the role-based security models of other technologies.</span></span>

 <span data-ttu-id="4877d-107">セキュリティ拡張機能はオープンで拡張可能な API に基づいているので、認証と承認の新しい拡張機能を [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] に作成できます。</span><span class="sxs-lookup"><span data-stu-id="4877d-107">Because security extensions are based on an open and extensible API, you can create new authentication and authorization extensions in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="4877d-108">以下は、フォームベースの認証と承認を使用する一般的なセキュリティ拡張機能の実装例です。</span><span class="sxs-lookup"><span data-stu-id="4877d-108">The following is an example of a typical security extension implementation that uses Forms-based authentication and authorization:</span></span>

 <span data-ttu-id="4877d-109">![Reporting Services のセキュリティ拡張フロー](../../media/rosettasecurityextensionflow.gif "Reporting Services のセキュリティ拡張フロー")</span><span class="sxs-lookup"><span data-stu-id="4877d-109">![Reporting Services security extension process](../../media/rosettasecurityextensionflow.gif "Reporting Services security extension process")</span></span>

 <span data-ttu-id="4877d-110">図に示すように、認証と承認は次のように行われます。</span><span class="sxs-lookup"><span data-stu-id="4877d-110">As shown in the illustration, authentication and authorization occur as follows:</span></span>

1.  <span data-ttu-id="4877d-111">ユーザーが URL を使用してレポート マネージャーへのアクセスを試行します。このユーザーは、クライアント アプリケーションに必要なユーザー資格情報を収集するフォームにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="4877d-111">A user tries to access Report Manager by using a URL and is redirected to a form that collects user credentials for the client application.</span></span>

2.  <span data-ttu-id="4877d-112">ユーザーが資格情報をフォームに送信します。</span><span class="sxs-lookup"><span data-stu-id="4877d-112">The user submits credentials to the form.</span></span>

3.  <span data-ttu-id="4877d-113">ユーザー資格情報は、<xref:ReportService2010.ReportingService2010.LogonUser%2A> メソッドによって Reporting Services Web サービスに送信されます。</span><span class="sxs-lookup"><span data-stu-id="4877d-113">The user credentials are submitted to the Reporting Services Web service through the <xref:ReportService2010.ReportingService2010.LogonUser%2A> method.</span></span>

4.  <span data-ttu-id="4877d-114">Web サービスは顧客指定のセキュリティ拡張機能を呼び出し、カスタム セキュリティ機関に存在するユーザー名とパスワードを検証します。</span><span class="sxs-lookup"><span data-stu-id="4877d-114">The Web service calls the customer-supplied security extension and verifies that the user name and password exist in the custom security authority.</span></span>

5.  <span data-ttu-id="4877d-115">認証後、Web サービスは認証チケット (クッキー) を作成、管理し、レポート マネージャーのホーム ページに対するユーザーのロールを検証します。</span><span class="sxs-lookup"><span data-stu-id="4877d-115">After authentication, the Web service creates an authentication ticket (known as a "cookie"), manages the ticket, and verifies the user's role for the Home page of Report Manager.</span></span>

6.  <span data-ttu-id="4877d-116">Web サービスがクッキーをブラウザーに返し、レポート マネージャーに適切なユーザー インターフェイスを表示します。</span><span class="sxs-lookup"><span data-stu-id="4877d-116">The Web service returns the cookie to the browser and displays the appropriate user interface in Report Manager.</span></span>

7.  <span data-ttu-id="4877d-117">ユーザーの認証後、HTTP ヘッダーにクッキーを追加して転送する際、ブラウザーはレポート マネージャーに要求を発信します。</span><span class="sxs-lookup"><span data-stu-id="4877d-117">After the user is authenticated, the browser makes requests to Report Manager while transmitting the cookie in the HTTP header.</span></span> <span data-ttu-id="4877d-118">これらの要求は、レポート マネージャー アプリケーション内でユーザーが行った操作に対応しています。</span><span class="sxs-lookup"><span data-stu-id="4877d-118">These requests are in response to user actions within the Report Manager application.</span></span>

8.  <span data-ttu-id="4877d-119">HTTP ヘッダーのクッキーは、要求されたユーザー操作と共に Web サービスに転送されます。</span><span class="sxs-lookup"><span data-stu-id="4877d-119">The cookie is transmitted in the HTTP header to the Web service along with the requested user operation.</span></span>

9. <span data-ttu-id="4877d-120">クッキーの有効性が確認された場合は、レポート サーバーがセキュリティ記述子を返します。さらに、要求された操作に関するレポート サーバー データベースからの情報を返します。</span><span class="sxs-lookup"><span data-stu-id="4877d-120">The cookie is validated, and if it is valid, the report server returns the security descriptor and other information relating to the requested operation from the report server database.</span></span>

10. <span data-ttu-id="4877d-121">クッキーが有効な場合、レポート サーバーはセキュリティ拡張機能を呼び出して、ユーザーが特定の操作の実行を許可されているかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="4877d-121">If the cookie is valid, the report server makes a call to the security extension to check if the user is authorized to perform the specific operation.</span></span>

11. <span data-ttu-id="4877d-122">ユーザーに許可が与えられている場合、レポート サーバーは要求された操作を実行して、呼び出し元に制御を返します。</span><span class="sxs-lookup"><span data-stu-id="4877d-122">If the user is authorized, the report server performs the requested operation and returns control to the caller.</span></span>

12. <span data-ttu-id="4877d-123">ユーザーの認証後、レポート サーバーへの URL アクセスでは常に同じクッキーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="4877d-123">After the user is authenticated, URL access to the report server uses the same cookie.</span></span> <span data-ttu-id="4877d-124">クッキーは、HTTP ヘッダーの一部として転送されます。</span><span class="sxs-lookup"><span data-stu-id="4877d-124">The cookie is transmitted in the HTTP header.</span></span>

13. <span data-ttu-id="4877d-125">セッションが終了するまで、ユーザーは引き続き、レポート サーバーに対する操作を要求します。</span><span class="sxs-lookup"><span data-stu-id="4877d-125">The user continues to request operations on the report server until the session has ended.</span></span>

## <a name="when-to-implement-a-security-extension"></a><span data-ttu-id="4877d-126">セキュリティ拡張機能を実装すべき状況</span><span class="sxs-lookup"><span data-stu-id="4877d-126">When to Implement a Security Extension</span></span>
 <span data-ttu-id="4877d-127">可能な限り Windows 認証を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4877d-127">We recommend that you use Windows Authentication if at all possible.</span></span> <span data-ttu-id="4877d-128">ただし、次の場合は、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] でカスタム認証と承認を使用した方が適していることがあります。</span><span class="sxs-lookup"><span data-stu-id="4877d-128">However, custom authentication and authorization for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] may be appropriate in the following two cases:</span></span>

-   <span data-ttu-id="4877d-129">Windows アカウントを使用できないインターネット アプリケーションまたはエクストラネット アプリケーションを実行する。</span><span class="sxs-lookup"><span data-stu-id="4877d-129">You have an Internet or extranet application that cannot use Windows accounts.</span></span>

-   <span data-ttu-id="4877d-130">ユーザーとロールを独自に定義しており、それに合わせた承認方法を [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] で使用する必要がある。</span><span class="sxs-lookup"><span data-stu-id="4877d-130">You have custom-defined users and roles and need to provide a matching authorization scheme in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="4877d-131">参照</span><span class="sxs-lookup"><span data-stu-id="4877d-131">See Also</span></span>
 <span data-ttu-id="4877d-132">[セキュリティ拡張機能の実装](../security-extension/implementing-a-security-extension.md)[カスタム認証クッキーを渡すようにレポートマネージャーを構成](../../security/configure-the-web-portal-to-pass-custom-authentication-cookies.md)する</span><span class="sxs-lookup"><span data-stu-id="4877d-132">[Implementing a Security Extension](../security-extension/implementing-a-security-extension.md) [Configure Report Manager to Pass Custom Authentication Cookies](../../security/configure-the-web-portal-to-pass-custom-authentication-cookies.md)</span></span>



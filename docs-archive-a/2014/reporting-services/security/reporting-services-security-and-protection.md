---
title: Reporting Services のセキュリティと保護 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- security [Reporting Services]
- Reporting Services, security
ms.assetid: 270075c5-bf12-4467-a775-abbda3d954a5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0f8c7a4186c5236260fb27d8de107ce8c97bd363
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644826"
---
# <a name="reporting-services-security-and-protection"></a><span data-ttu-id="8c132-102">Reporting Services のセキュリティと保護</span><span class="sxs-lookup"><span data-stu-id="8c132-102">Reporting Services Security and Protection</span></span>
  <span data-ttu-id="8c132-103">このセクションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]のセキュリティ機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="8c132-103">You can use information in this section to learn about the security features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="8c132-104">また、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]でサポートされている承認モデルと認証プロバイダーについても説明します。</span><span class="sxs-lookup"><span data-stu-id="8c132-104">This section also explains the authorization models and authentication providers supported in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
## <a name="extended-protection-for-authentication"></a><span data-ttu-id="8c132-105">認証の拡張保護 (Extended Protection for Authentication)</span><span class="sxs-lookup"><span data-stu-id="8c132-105">Extended Protection for Authentication</span></span>  
 <span data-ttu-id="8c132-106">[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]以降では、認証の拡張保護がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8c132-106">Beginning with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], support for Extended Protection for Authentication is available.</span></span> <span data-ttu-id="8c132-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能により、認証の拡張保護に対するチャネル バインドとサービス バインドの使用がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="8c132-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] feature supports the use of channel binding and service binding to enhance protection of authentication.</span></span> <span data-ttu-id="8c132-108">この [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能は、拡張保護がサポートされているオペレーティング システムで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c132-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features need to be used with an operating system that supports Extended Protection.</span></span> <span data-ttu-id="8c132-109">詳細については、「 [Reporting Services での認証の拡張保護](extended-protection-for-authentication-with-reporting-services.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8c132-109">For more information, see [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md).</span></span>  
  
## <a name="authentication-and-authorization"></a><span data-ttu-id="8c132-110">認証と承認</span><span class="sxs-lookup"><span data-stu-id="8c132-110">Authentication and Authorization</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="8c132-111">では、レポート サーバーで認証を行うためのさまざまな認証の種類が、ユーザーおよびクライアント アプリケーションに提供されます。</span><span class="sxs-lookup"><span data-stu-id="8c132-111">provides different authentication types for users and client applications to authenticate with the report server.</span></span> <span data-ttu-id="8c132-112">レポート サーバーの適切な認証の種類を使用すると、組織で必要とされる適切なレベルのセキュリティを実現できます。</span><span class="sxs-lookup"><span data-stu-id="8c132-112">Using the right authentication type for your report server enables your organization to achieve the appropriate level of security required by your organization.</span></span> <span data-ttu-id="8c132-113">詳細については、「 [レポート サーバーでの認証](authentication-with-the-report-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c132-113">For more information, see [Authentication with the Report Server](authentication-with-the-report-server.md).</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="8c132-114">では、レポート サーバー カタログ内のコンテンツへのユーザー アクセス (つまり、アクセスできるユーザーとそのユーザーがアクセスできるコンテンツ、およびアクセス方法) を制御するためのロールと権限も使用されます。</span><span class="sxs-lookup"><span data-stu-id="8c132-114">also employs roles and permissions to control user access to content in the report server catalog (in other words, who can access what, and how s/he can access it).</span></span> <span data-ttu-id="8c132-115">詳細については、「[ロールと権限 (Reporting Services)](roles-and-permissions-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c132-115">For more information, see [Roles and Permissions &#40;Reporting Services&#41;](roles-and-permissions-reporting-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="8c132-116">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="8c132-116">Related Tasks</span></span>  
  
|<span data-ttu-id="8c132-117">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="8c132-117">Task Descriptions</span></span>|<span data-ttu-id="8c132-118">リンク</span><span class="sxs-lookup"><span data-stu-id="8c132-118">Links</span></span>|  
|-----------------------|-----------|  
|<span data-ttu-id="8c132-119">レポート サーバーへのクライアント接続を保護するための Secure Socket Layer (SSL) の構成</span><span class="sxs-lookup"><span data-stu-id="8c132-119">Configure the Secure Socket Layer (SSL) to secure client connections to the report server.</span></span>|[<span data-ttu-id="8c132-120">ネイティブ モードのレポート サーバーでの SSL 接続の構成</span><span class="sxs-lookup"><span data-stu-id="8c132-120">Configure SSL Connections on a Native Mode Report Server</span></span>](configure-ssl-connections-on-a-native-mode-report-server.md)|  
  
  

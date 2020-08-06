---
title: Reporting Services SharePoint モード認証 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade SharePoint Mode [Reporting Services]
- SharePoint integration
- SharePoint Mode
ms.assetid: 2c19794a-dd55-4fe5-b901-6dd93e9f6beb
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3b1316a1a49726ab0754f39160125425fec116d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737536"
---
# <a name="reporting-services-sharepoint-mode-authentication"></a><span data-ttu-id="cefd6-102">Reporting Services SharePoint モード認証</span><span class="sxs-lookup"><span data-stu-id="cefd6-102">Reporting Services SharePoint Mode Authentication</span></span>
  <span data-ttu-id="cefd6-103">\*\*\*\* インストール ウィザードの [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ページを使用すると、現在の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インストールで使用されるサービス アカウントの資格情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="cefd6-103">Use the **Reporting Services SharePoint Mode Authentication** page of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard to specify the credentials of the service account that is used in the current [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation.</span></span> <span data-ttu-id="cefd6-104">資格情報は新しい SharePoint アプリケーション プールの作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="cefd6-104">The credentials will be used to create a new SharePoint application pool.</span></span> <span data-ttu-id="cefd6-105">また、1 つの新しい [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint サービス アプリケーションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="cefd6-105">Also, one new [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint service application will be created.</span></span> <span data-ttu-id="cefd6-106">サービス アプリケーション名には前の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インスタンス名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="cefd6-106">The service application name will contain the name of the previous [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance name.</span></span>  
  
## <a name="options"></a><span data-ttu-id="cefd6-107">Options</span><span class="sxs-lookup"><span data-stu-id="cefd6-107">Options</span></span>  
  
-   <span data-ttu-id="cefd6-108">**[SSRS アプリケーション プールのアカウント名]** オプションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="cefd6-108">The **SSRS Application Pool Account Name:** option is read only.</span></span> <span data-ttu-id="cefd6-109">値はアップグレード中の既存の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インストールからの現在の値で自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="cefd6-109">The value is automatically populated with the current value from the existing [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation that you are upgrading.</span></span>  
  
-   <span data-ttu-id="cefd6-110">アプリケーション プール アカウントのパスワードが不要な場合、 **[SSRS アプリケーション プール アカウントのパスワード]** オプションは無効になります。</span><span class="sxs-lookup"><span data-stu-id="cefd6-110">The **SSRS Application Pool Account Password:** option will be disabled if the application pool account does not require a password.</span></span> <span data-ttu-id="cefd6-111">たとえば、"NT Authority\NetworkService" のようになります。</span><span class="sxs-lookup"><span data-stu-id="cefd6-111">For example, "NT Authority\NetworkService".</span></span> <span data-ttu-id="cefd6-112">アプリケーション プール アカウントのパスワードが必要な場合、正しいパスワードを入力するまでアップグレードは続行できません。</span><span class="sxs-lookup"><span data-stu-id="cefd6-112">If the application pool account does require a password, you cannot continue with upgrade until you type the correct password.</span></span>  
  
 <span data-ttu-id="cefd6-113">詳細については、「 [Reporting Services のアップグレードと移行](https://go.microsoft.com/fwlink/?LinkID=245628)」 (を参照してください https://go.microsoft.com/fwlink/?LinkID=245628) 。</span><span class="sxs-lookup"><span data-stu-id="cefd6-113">For more information, see [Upgrade and Migrate Reporting Services](https://go.microsoft.com/fwlink/?LinkID=245628) (https://go.microsoft.com/fwlink/?LinkID=245628).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cefd6-114">参照</span><span class="sxs-lookup"><span data-stu-id="cefd6-114">See Also</span></span>  
 [<span data-ttu-id="cefd6-115">Reporting Services のアップグレードと移行</span><span class="sxs-lookup"><span data-stu-id="cefd6-115">Upgrade and Migrate Reporting Services</span></span>](https://go.microsoft.com/fwlink/?LinkID=245628)  
  
  

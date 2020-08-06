---
title: カスタム認証 Cookie を渡すようにレポートマネージャーを構成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- authentication [Reporting Services]
- extensions [Reporting Services], custom security
ms.assetid: 91aeb053-149e-4562-ae4c-a688d0e1b2ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 90e8798fb91152ec64e7f290dc1522fc8eaa451c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633720"
---
# <a name="configure-report-manager-to-pass-custom-authentication-cookies"></a><span data-ttu-id="65ce8-102">カスタム認証クッキーを送信するようにレポート マネージャーを構成する</span><span class="sxs-lookup"><span data-stu-id="65ce8-102">Configure Report Manager to Pass Custom Authentication Cookies</span></span>
  <span data-ttu-id="65ce8-103">カスタム認証拡張機能を使用している場合、カスタム認証クッキーを送信するようにレポート マネージャーを構成してください。</span><span class="sxs-lookup"><span data-stu-id="65ce8-103">If you are using a custom authentication extension, you should configure Report Manager to transmit custom authentication cookies.</span></span> <span data-ttu-id="65ce8-104">構成しない場合、レポート マネージャーはレポート サーバー固有の HTTP 要求を使用してクッキーを送信するだけです。</span><span class="sxs-lookup"><span data-stu-id="65ce8-104">Otherwise, Report Manager will only transmit cookies through HTTP requests specific to the report server.</span></span> <span data-ttu-id="65ce8-105">追加のクッキーを送信するには、RSReportServer.Config ファイルを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65ce8-105">If you want to transmit additional cookies, you must modify the RSReportServer.Config file.</span></span>  
  
## <a name="modifying-the-rsreportserverconfig-file"></a><span data-ttu-id="65ce8-106">RSReportServer.Config ファイルの変更</span><span class="sxs-lookup"><span data-stu-id="65ce8-106">Modifying the RSReportServer.Config File</span></span>  
 <span data-ttu-id="65ce8-107">レポートマネージャーを有効にすると、 `PassThroughCookies` RSReportServer.config ファイルのレポートマネージャー構成設定に <> 要素を追加することにより、レポートサーバーに追加のクッキーを送信することができます。</span><span class="sxs-lookup"><span data-stu-id="65ce8-107">You can enable Report Manager to transmit additional cookies through to the report server by adding a <`PassThroughCookies`> element to the Report Manager configuration settings in the RSReportServer.config file.</span></span> <span data-ttu-id="65ce8-108">追加のクッキーの送信は、レポート サーバーの認証クッキーだけでなく、サード パーティの認証システムのクッキーも必要なシングル サインオン認証ソリューションで便利です。</span><span class="sxs-lookup"><span data-stu-id="65ce8-108">Transmitting additional cookies is helpful in a single sign-on authentication solution that requires not only the report server authentication cookies, but also cookies from a third-party authentication system.</span></span>  
  
 <span data-ttu-id="65ce8-109">レポート マネージャーの使用時に HTTP 要求を使用した追加のクッキーの送信を有効にするには、RSReportServer.config ファイルに次の要素を設定してください。</span><span class="sxs-lookup"><span data-stu-id="65ce8-109">To enable additional cookies to be transmitted through HTTP requests when using Report Manager, set the following elements in the RSReportServer.config file:</span></span>  
  
```  
<UI>  
   <CustomAuthenticationUI>  
      ...  
      <PassThroughCookies>  
         <PassThroughCookie>cookiename1</PassThroughCookie>  
         <PassThroughCookie>cookiename2</PassThroughCookie>  
      </PassThroughCookies>  
   </CustomAuthenticationUI>  
      ...  
</UI>  
```  
  
## <a name="see-also"></a><span data-ttu-id="65ce8-110">参照</span><span class="sxs-lookup"><span data-stu-id="65ce8-110">See Also</span></span>  
 <span data-ttu-id="65ce8-111">[レポート サーバーでの認証](authentication-with-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="65ce8-111">[Authentication with the Report Server](authentication-with-the-report-server.md) </span></span>  
 <span data-ttu-id="65ce8-112">[RSReportServer 構成ファイル](../report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="65ce8-112">[RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="65ce8-113">[セキュリティ拡張機能の概要](../extensions/security-extension/security-extensions-overview.md) </span><span class="sxs-lookup"><span data-stu-id="65ce8-113">[Security Extensions Overview](../extensions/security-extension/security-extensions-overview.md) </span></span>  
 [<span data-ttu-id="65ce8-114">レポート サーバーを構成および管理する &#40;SSRSネイティブ モード&#41;</span><span class="sxs-lookup"><span data-stu-id="65ce8-114">Configure and Administer a Report Server &#40;SSRS Native Mode&#41;</span></span>](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
  
  

---
title: Reporting Services 配信拡張機能の設定 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- XML Web service [Reporting Services], delivery extension settings
- Report Server Web service, delivery extension settings
- delivery [Reporting Services]
- network share delivery [Reporting Services]
- file share delivery [Reporting Services]
- e-mail [Reporting Services]
- mailing reports [Reporting Services]
- sharing reports
- extensions [Reporting Services], delivery
- mail [Reporting Services]
- Web service [Reporting Services], delivery extension settings
ms.assetid: 68c31a85-261c-4ec4-b8df-1f9842b46f8a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d5363c99cb858ce61f7be3b039e27a69944767b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713806"
---
# <a name="reporting-services-delivery-extension-settings"></a><span data-ttu-id="06e38-102">Reporting Services 配信拡張機能の設定</span><span class="sxs-lookup"><span data-stu-id="06e38-102">Reporting Services Delivery Extension Settings</span></span>
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="06e38-103">には、電子メールの配信拡張機能とファイル共有の配信拡張機能があります。</span><span class="sxs-lookup"><span data-stu-id="06e38-103">includes an e-mail delivery extension and a file share delivery extension.</span></span> <span data-ttu-id="06e38-104">電子メールの配信拡張機能では、電子メールを使用して、個々のユーザーやグループにレポートを送信できます。</span><span class="sxs-lookup"><span data-stu-id="06e38-104">E-mail delivery provides a way to send a report to individual users or groups through e-mail.</span></span> <span data-ttu-id="06e38-105">ファイル共有の配信機能では、生成したレポートをネットワーク上の共有者に自動的に送信できます。</span><span class="sxs-lookup"><span data-stu-id="06e38-105">File share delivery enables you to automatically send rendered reports to a share on your network.</span></span> <span data-ttu-id="06e38-106">サポートされているいずれかの配信拡張機能を、標準的なサブスクリプションまたはデータ ドリブン サブスクリプションと一緒に使用できます。</span><span class="sxs-lookup"><span data-stu-id="06e38-106">You can use either one of the supported delivery extensions with standard subscriptions or data-driven subscriptions.</span></span> <span data-ttu-id="06e38-107"><xref:ReportService2010.ReportingService2010.CreateSubscription%2A> メソッド、<xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A> メソッド、<xref:ReportService2010.ReportingService2010.SetSubscriptionProperties%2A> メソッド、および <xref:ReportService2010.ReportingService2010.SetDataDrivenSubscriptionProperties%2A> メソッドを呼び出すときは常に、配信拡張機能の種類に固有の配信設定を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="06e38-107">You pass delivery settings that are specific to the type of delivery extension whenever you call the <xref:ReportService2010.ReportingService2010.CreateSubscription%2A>,<xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A>,<xref:ReportService2010.ReportingService2010.SetSubscriptionProperties%2A>, and <xref:ReportService2010.ReportingService2010.SetDataDrivenSubscriptionProperties%2A> methods.</span></span> <span data-ttu-id="06e38-108">配信設定の一覧をプログラムによって取得するには、<xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="06e38-108">To retrieve a list of delivery settings programmatically, use the <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A> method.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="06e38-109">配信拡張機能の設定では、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="06e38-109">Delivery extension settings are case-sensitive.</span></span>  
  
## <a name="e-mail-delivery-settings"></a><span data-ttu-id="06e38-110">電子メール配信の設定</span><span class="sxs-lookup"><span data-stu-id="06e38-110">E-Mail Delivery Settings</span></span>  
 <span data-ttu-id="06e38-111">次の表は、レポート サーバー電子メールを使用するサブスクリプションの電子メール配信設定を示しています。</span><span class="sxs-lookup"><span data-stu-id="06e38-111">The following table lists the e-mail delivery settings for subscriptions that use report server e-mail.</span></span>  
  
|<span data-ttu-id="06e38-112">設定</span><span class="sxs-lookup"><span data-stu-id="06e38-112">Setting</span></span>|<span data-ttu-id="06e38-113">値</span><span class="sxs-lookup"><span data-stu-id="06e38-113">Value</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="06e38-114">**宛先**</span><span class="sxs-lookup"><span data-stu-id="06e38-114">**TO**</span></span>|<span data-ttu-id="06e38-115">電子メール メッセージの `To` 行に表示される電子メール アドレス。</span><span class="sxs-lookup"><span data-stu-id="06e38-115">The e-mail address that appears on the `To` line of the e-mail message.</span></span> <span data-ttu-id="06e38-116">複数の電子メール アドレスを指定するときは、それぞれをセミコロンで区切ります。</span><span class="sxs-lookup"><span data-stu-id="06e38-116">Multiple e-mail addresses are separated by semicolons.</span></span> <span data-ttu-id="06e38-117">必須。</span><span class="sxs-lookup"><span data-stu-id="06e38-117">Required.</span></span>|  
|<span data-ttu-id="06e38-118">**問い合わせ**</span><span class="sxs-lookup"><span data-stu-id="06e38-118">**CC**</span></span>|<span data-ttu-id="06e38-119">電子メール メッセージの `Cc` 行に表示される電子メール アドレス。</span><span class="sxs-lookup"><span data-stu-id="06e38-119">The e-mail address that appears on the `Cc` line of the e-mail message.</span></span> <span data-ttu-id="06e38-120">複数の電子メール アドレスを指定するときは、それぞれをセミコロンで区切ります。</span><span class="sxs-lookup"><span data-stu-id="06e38-120">Multiple e-mail addresses are separated by semicolons.</span></span> <span data-ttu-id="06e38-121">省略可能。</span><span class="sxs-lookup"><span data-stu-id="06e38-121">Optional.</span></span>|  
|<span data-ttu-id="06e38-122">**BCC**</span><span class="sxs-lookup"><span data-stu-id="06e38-122">**BCC**</span></span>|<span data-ttu-id="06e38-123">電子メール メッセージの `Bcc` 行に表示される電子メール アドレス。</span><span class="sxs-lookup"><span data-stu-id="06e38-123">The e-mail address that appears on the `Bcc` line of the e-mail message.</span></span> <span data-ttu-id="06e38-124">複数の電子メール アドレスを指定するときは、それぞれをセミコロンで区切ります。</span><span class="sxs-lookup"><span data-stu-id="06e38-124">Multiple e-mail addresses are separated by semicolons.</span></span> <span data-ttu-id="06e38-125">省略可能。</span><span class="sxs-lookup"><span data-stu-id="06e38-125">Optional.</span></span>|  
|<span data-ttu-id="06e38-126">**ReplyTo**</span><span class="sxs-lookup"><span data-stu-id="06e38-126">**ReplyTo**</span></span>|<span data-ttu-id="06e38-127">電子メール メッセージの `Reply-To` ヘッダーに表示される電子メール アドレス。</span><span class="sxs-lookup"><span data-stu-id="06e38-127">The e-mail address that appears in the `Reply-To` header of the e-mail message.</span></span> <span data-ttu-id="06e38-128">値は、電子メール アドレス 1 つである必要があります。</span><span class="sxs-lookup"><span data-stu-id="06e38-128">The value must be a single e-mail address.</span></span> <span data-ttu-id="06e38-129">省略可能。</span><span class="sxs-lookup"><span data-stu-id="06e38-129">Optional.</span></span>|  
|`IncludeReport`|<span data-ttu-id="06e38-130">電子メール配信にレポートを含めるかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="06e38-130">A value that indicates whether to include the report in the e-mail delivery.</span></span> <span data-ttu-id="06e38-131">この値が `true` の場合は、レポートを電子メール メッセージの本文として配信することを示します。</span><span class="sxs-lookup"><span data-stu-id="06e38-131">A value of `true` indicates that the report is delivered in the body of the e-mail message.</span></span>|  
|<span data-ttu-id="06e38-132">**RenderFormat**</span><span class="sxs-lookup"><span data-stu-id="06e38-132">**RenderFormat**</span></span>|<span data-ttu-id="06e38-133">表示レポートの生成に使用する表示拡張機能の名前。</span><span class="sxs-lookup"><span data-stu-id="06e38-133">The name of the rendering extension to use to generate the rendered report.</span></span> <span data-ttu-id="06e38-134">名前は、レポート サーバーにインストールされている表示可能な表示拡張機能のいずれかに対応している必要があります。</span><span class="sxs-lookup"><span data-stu-id="06e38-134">The name must correspond to one of the visible rendering extensions installed on the report server.</span></span> <span data-ttu-id="06e38-135">`IncludeReport` の設定値が `true` の場合は、この値を必ず指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="06e38-135">This value is required if the `IncludeReport` setting is set to a value of `true`.</span></span>|  
|<span data-ttu-id="06e38-136">**優先順位**</span><span class="sxs-lookup"><span data-stu-id="06e38-136">**Priority**</span></span>|<span data-ttu-id="06e38-137">電子メール メッセージを送信する優先順位。</span><span class="sxs-lookup"><span data-stu-id="06e38-137">The priority with which the e-mail message is sent.</span></span> <span data-ttu-id="06e38-138">有効な値は `LOW`、`NORMAL`、`HIGH` です。</span><span class="sxs-lookup"><span data-stu-id="06e38-138">Valid values are `LOW`, `NORMAL`, and `HIGH`.</span></span> <span data-ttu-id="06e38-139">既定値は `NORMAL` です。</span><span class="sxs-lookup"><span data-stu-id="06e38-139">The default value is `NORMAL`.</span></span>|  
|<span data-ttu-id="06e38-140">**件名**</span><span class="sxs-lookup"><span data-stu-id="06e38-140">**Subject**</span></span>|<span data-ttu-id="06e38-141">電子メール メッセージの件名のテキスト。</span><span class="sxs-lookup"><span data-stu-id="06e38-141">The text in the subject line of the e-mail message.</span></span>|  
|<span data-ttu-id="06e38-142">**コメント**</span><span class="sxs-lookup"><span data-stu-id="06e38-142">**Comment**</span></span>|<span data-ttu-id="06e38-143">電子メール メッセージの本文のテキスト。</span><span class="sxs-lookup"><span data-stu-id="06e38-143">The text included in the body of the e-mail message.</span></span>|  
|<span data-ttu-id="06e38-144">**IncludeLink**</span><span class="sxs-lookup"><span data-stu-id="06e38-144">**IncludeLink**</span></span>|<span data-ttu-id="06e38-145">電子メールの本文にレポートへのリンクを含めるかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="06e38-145">A value that indicates whether to include a link to the report in the body of the e-mail.</span></span>|  
  
## <a name="file-share-delivery-settings"></a><span data-ttu-id="06e38-146">ファイル共有配信の設定</span><span class="sxs-lookup"><span data-stu-id="06e38-146">File Share Delivery Settings</span></span>  
 <span data-ttu-id="06e38-147">次の表は、サブスクリプションのファイル共有配信設定を示しています。</span><span class="sxs-lookup"><span data-stu-id="06e38-147">The following table lists the file share delivery settings for subscriptions.</span></span>  
  
|<span data-ttu-id="06e38-148">設定</span><span class="sxs-lookup"><span data-stu-id="06e38-148">Setting</span></span>|<span data-ttu-id="06e38-149">値</span><span class="sxs-lookup"><span data-stu-id="06e38-149">Value</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="06e38-150">**/DB**</span><span class="sxs-lookup"><span data-stu-id="06e38-150">**FILENAME**</span></span>|<span data-ttu-id="06e38-151">ディスクに保存するファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="06e38-151">The name of the file that is saved to disk.</span></span>|  
|<span data-ttu-id="06e38-152">**FILEEXTN**</span><span class="sxs-lookup"><span data-stu-id="06e38-152">**FILEEXTN**</span></span>|<span data-ttu-id="06e38-153">表示レポートのファイル拡張機能を含めるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="06e38-153">Indicates whether to include a file extension for the rendered report.</span></span> <span data-ttu-id="06e38-154">値は `true` または `false` です。</span><span class="sxs-lookup"><span data-stu-id="06e38-154">The value is either `true` or `false`.</span></span>|  
|<span data-ttu-id="06e38-155">**PATH**</span><span class="sxs-lookup"><span data-stu-id="06e38-155">**PATH**</span></span>|<span data-ttu-id="06e38-156">レポートを保存するフォルダー パスまたは UNC ファイル共有パス。</span><span class="sxs-lookup"><span data-stu-id="06e38-156">The folder path or UNC file share path to which to save the report.</span></span>|  
|<span data-ttu-id="06e38-157">**RENDER_FORMAT**</span><span class="sxs-lookup"><span data-stu-id="06e38-157">**RENDER_FORMAT**</span></span>|<span data-ttu-id="06e38-158">ディスクに保存するレポートの形式。</span><span class="sxs-lookup"><span data-stu-id="06e38-158">The format of the report that is saved to disk.</span></span>|  
|<span data-ttu-id="06e38-159">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="06e38-159">**USERNAME**</span></span>|<span data-ttu-id="06e38-160">ネットワーク リソースまたはディスクへのアクセスに必要なユーザー名。</span><span class="sxs-lookup"><span data-stu-id="06e38-160">The username required to access the network resource or disk.</span></span>|  
|<span data-ttu-id="06e38-161">**入力**</span><span class="sxs-lookup"><span data-stu-id="06e38-161">**PASSWORD**</span></span>|<span data-ttu-id="06e38-162">ネットワーク リソースまたはディスクへのアクセスに必要なパスワード。</span><span class="sxs-lookup"><span data-stu-id="06e38-162">The password required to access the network resource or disk.</span></span>|  
|<span data-ttu-id="06e38-163">**WRITEMODE**</span><span class="sxs-lookup"><span data-stu-id="06e38-163">**WRITEMODE**</span></span>|<span data-ttu-id="06e38-164">ディスクへのアクセスに使用する書き込みモード。</span><span class="sxs-lookup"><span data-stu-id="06e38-164">The write mode to use when accessing the disk.</span></span> <span data-ttu-id="06e38-165">有効な値は `None`、`Overwrite`、`AutoIncrement` です。</span><span class="sxs-lookup"><span data-stu-id="06e38-165">Valid values are `None`, `Overwrite`, and `AutoIncrement`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="06e38-166">参照</span><span class="sxs-lookup"><span data-stu-id="06e38-166">See Also</span></span>  
 <span data-ttu-id="06e38-167">[SSRS&#41;&#40;テクニカルリファレンス](../../technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="06e38-167">[Technical Reference &#40;SSRS&#41;](../../technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="06e38-168">Web サービスと .NET Framework を使用してのアプリケーションの構築</span><span class="sxs-lookup"><span data-stu-id="06e38-168">Building Applications Using the Web Service and the .NET Framework</span></span>](building-applications-using-the-web-service-and-the-net-framework.md)  
  
  

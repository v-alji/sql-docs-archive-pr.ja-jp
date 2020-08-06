---
title: レポートの配布を制御する |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], report distribution
- subscriptions [Reporting Services], e-mail
- subscriptions [Reporting Services], file share delivery
- file share delivery [Reporting Services]
- e-mail [Reporting Services]
- subscriptions [Reporting Services], security
- mail [Reporting Services]
ms.assetid: 8f15e2c6-a647-4b05-a519-1743b5d8654c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: de8a27801ef89f10bf303cee17d1c2d0e1081c5a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630808"
---
# <a name="control-report-distribution"></a><span data-ttu-id="4ea8c-102">レポートの配信を制御する</span><span class="sxs-lookup"><span data-stu-id="4ea8c-102">Control Report Distribution</span></span>
  <span data-ttu-id="4ea8c-103">電子メール配信およびファイル共有配信に関連するセキュリティ上のリスクを減らすように、レポート サーバーを構成できます。</span><span class="sxs-lookup"><span data-stu-id="4ea8c-103">You can configure a report server to reduce the security risks associated with e-mail and file share distribution.</span></span>  
  
## <a name="securing-reports"></a><span data-ttu-id="4ea8c-104">レポートの保護</span><span class="sxs-lookup"><span data-stu-id="4ea8c-104">Securing Reports</span></span>  
 <span data-ttu-id="4ea8c-105">レポートの配信を制御する際の最初の手順は、承認されていないアクセスからレポートをセキュリティで保護することです。</span><span class="sxs-lookup"><span data-stu-id="4ea8c-105">The first step in controlling report distribution is to secure the report against unauthorized access.</span></span> <span data-ttu-id="4ea8c-106">レポートでは、サブスクリプションで使用するために、配信ごとに変化しない格納済み資格情報セットを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ea8c-106">To be used in a subscription, a report must use a stored set of credentials that do not vary for individual deliveries.</span></span> <span data-ttu-id="4ea8c-107">レポート サーバー上のレポートにアクセスできるユーザーなら、だれでもレポートを実行でき、場合によってはレポートを配信することもできます。</span><span class="sxs-lookup"><span data-stu-id="4ea8c-107">Any user who can access the report on the report server can run it and possibly distribute it.</span></span> <span data-ttu-id="4ea8c-108">このようなことが発生しないように、この操作を必要とするユーザーのみにレポート アクセスを制限する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ea8c-108">To prevent this from occurring, you must limit report access to only those users who require it.</span></span> <span data-ttu-id="4ea8c-109">詳細については、「[レポートとリソースの保護](security/secure-reports-and-resources.md)」および「[セキュリティ保護されたフォルダー](security/secure-folders.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ea8c-109">For more information, see [Secure Reports and Resources](security/secure-reports-and-resources.md) and [Secure Folders](security/secure-folders.md).</span></span>  
  
 <span data-ttu-id="4ea8c-110">データベース セキュリティを使用してアクセスを承認する、高い機密情報を含むレポートは、サブスクリプションとして配信することはできません。</span><span class="sxs-lookup"><span data-stu-id="4ea8c-110">Highly confidential reports that use database security to authorize access cannot be distributed by way of subscription.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4ea8c-111">レポートはファイルとして転送されます。</span><span class="sxs-lookup"><span data-stu-id="4ea8c-111">Reports are transported as files.</span></span> <span data-ttu-id="4ea8c-112">ファイルに適用されるリスクおよび保護方法は、ディスクに保存されるレポートまたは添付ファイルとして送信されるレポートにも同様に適用されます。</span><span class="sxs-lookup"><span data-stu-id="4ea8c-112">The risks and safeguards that apply to files apply equally to reports that are saved to disk or sent as attachments.</span></span> <span data-ttu-id="4ea8c-113">ファイルへのアクセス権を持つユーザーは、自己の判断でファイルを配布または使用できます。</span><span class="sxs-lookup"><span data-stu-id="4ea8c-113">Any user who has access to a file can distribute or use the file at his or her discretion.</span></span>  
  
## <a name="controlling-e-mail-delivery"></a><span data-ttu-id="4ea8c-114">電子メール配信の制御</span><span class="sxs-lookup"><span data-stu-id="4ea8c-114">Controlling E-Mail Delivery</span></span>  
 <span data-ttu-id="4ea8c-115">特定のホスト ドメインへの電子メールの配信を制限するようにレポート サーバーを構成できます。</span><span class="sxs-lookup"><span data-stu-id="4ea8c-115">You can configure a report server to limit e-mail distribution to specific host domains.</span></span> <span data-ttu-id="4ea8c-116">たとえば、RSReportServer 構成ファイルに一覧されたドメインを除くすべてのドメインに、レポート サーバーからレポートが配信されないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="4ea8c-116">For example, you can prevent a report server from delivering a report to all domains except those listed in the RSReportServer configuration file.</span></span>  
  
 <span data-ttu-id="4ea8c-117">また、サブスクリプションの **[宛先]** フィールドを非表示にするように構成を設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="4ea8c-117">You can also set configuration settings to hide the **To** field in a subscription.</span></span> <span data-ttu-id="4ea8c-118">この場合、レポートは、サブスクリプションを定義するユーザーにのみ配信されます。</span><span class="sxs-lookup"><span data-stu-id="4ea8c-118">In this case, reports are delivered only to the user defining the subscription.</span></span> <span data-ttu-id="4ea8c-119">ただし、レポートがユーザーに送信された後で、このレポートが転送されることを明示的に防ぐことはできません。</span><span class="sxs-lookup"><span data-stu-id="4ea8c-119">However, after a report is sent to a user, you cannot explicitly prevent it from being forwarded.</span></span>  
  
 <span data-ttu-id="4ea8c-120">レポートの配信を制御する最も効果的な方法は、レポート サーバーからレポート サーバーの URL のみを送信するように構成することです。</span><span class="sxs-lookup"><span data-stu-id="4ea8c-120">The most effective way to control report distribution is to configure a report server to send only a report server URL.</span></span> <span data-ttu-id="4ea8c-121">レポート サーバーでは、Windows 認証およびロールベースの承認モデルを使用して、レポートへのアクセスを制御します。</span><span class="sxs-lookup"><span data-stu-id="4ea8c-121">The report server uses Windows Authentication and a role-based authorization model to control access to a report.</span></span> <span data-ttu-id="4ea8c-122">ユーザーが表示権限のないレポートを電子メールで誤って受信しても、レポート サーバーはレポートを表示しません。</span><span class="sxs-lookup"><span data-stu-id="4ea8c-122">If a user accidentally receives through e-mail a report that he or she is not authorized to view, the report server will not display the report.</span></span>  
  
## <a name="controlling-file-share-delivery"></a><span data-ttu-id="4ea8c-123">ファイル共有の配信の制御</span><span class="sxs-lookup"><span data-stu-id="4ea8c-123">Controlling File Share Delivery</span></span>  
 <span data-ttu-id="4ea8c-124">ファイル共有の配信は、ハード ディスク上のファイルにレポートを送信する際に使用されます。</span><span class="sxs-lookup"><span data-stu-id="4ea8c-124">File share delivery is used to send a report to a file on a hard disk.</span></span> <span data-ttu-id="4ea8c-125">ファイルがディスクに保存されると、レポート サーバーはユーザー アクセスの制御にロールベースのセキュリティ モデルを使用する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="4ea8c-125">After the file has been saved to disk, it is no longer subject to the role-based security model that the report server uses to control user access.</span></span> <span data-ttu-id="4ea8c-126">ディスクに配信されたレポートを保護するために、ファイル自体またはそのファイルを含むフォルダーにアクセス制御リスト (ACL) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="4ea8c-126">To secure a report that has been delivered to disk, you can place Access Control Lists (ACLs) on the file itself or on the folder that contains it.</span></span> <span data-ttu-id="4ea8c-127">オペレーティング システムによっては、別のセキュリティ オプションを使用できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="4ea8c-127">Additional security options might be available, depending on your operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ea8c-128">参照</span><span class="sxs-lookup"><span data-stu-id="4ea8c-128">See Also</span></span>  
 <span data-ttu-id="4ea8c-129">[SSRS Configuration Manager &#40;電子メール配信用にレポートサーバーを構成&#41;](../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="4ea8c-129">[Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="4ea8c-130">[サブスクリプションと配信 &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="4ea8c-130">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md) </span></span>  
 [<span data-ttu-id="4ea8c-131">ネイティブ モード レポート サーバーのサブスクリプションの作成と管理</span><span class="sxs-lookup"><span data-stu-id="4ea8c-131">Create and Manage Subscriptions for Native Mode Report Servers</span></span>](../../2014/reporting-services/create-manage-subscriptions-native-mode-report-servers.md)  
  
  

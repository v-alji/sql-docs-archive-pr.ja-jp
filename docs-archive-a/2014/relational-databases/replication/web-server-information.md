---
title: Web サーバー情報 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.webserverinformation.f1
ms.assetid: 86d72275-45c7-459f-98cf-f5a366ed279c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f7b461ed26b3e234f083add3312e256e164efc9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634929"
---
# <a name="web-server-information"></a><span data-ttu-id="6922c-102">Web サーバー情報</span><span class="sxs-lookup"><span data-stu-id="6922c-102">Web Server Information</span></span>
  <span data-ttu-id="6922c-103">Web サーバー情報は、マージ レプリケーションの Web 同期オプションを使用する場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="6922c-103">Web server information is required to use the Web synchronization option for merge replication.</span></span> <span data-ttu-id="6922c-104">Web 同期の構成の詳細については、「[Configure Web Synchronization (Web 同期の構成)](configure-web-synchronization.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6922c-104">For information about configuring Web synchronization, see [Configure Web Synchronization](configure-web-synchronization.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="6922c-105">Options</span><span class="sxs-lookup"><span data-stu-id="6922c-105">Options</span></span>  
 <span data-ttu-id="6922c-106">**[Web サーバー アドレス]**</span><span class="sxs-lookup"><span data-stu-id="6922c-106">**Web server address**</span></span>  
 <span data-ttu-id="6922c-107">**[パブリケーションのプロパティ]** ダイアログ ボックスの **[FTP スナップショットとインターネット]** ページで Web サーバー アドレスを指定している場合は、そのアドレスがこのテキスト ボックスに既定として表示されます。</span><span class="sxs-lookup"><span data-stu-id="6922c-107">If you specified a Web server address in the **FTP Snapshot andInternet** page of the **Publication Properties** dialog box, it appears in this text box as a default.</span></span> <span data-ttu-id="6922c-108">既定値を受け入れるか、このサブスクリプションを同期する [!INCLUDE[msCoName](../../includes/msconame-md.md)] インターネット インフォメーション サービス (IIS) の完全修飾 Web サーバー アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="6922c-108">Either accept the default or enter a fully qualified Web server address for the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) server that synchronizes this subscription.</span></span>  
  
 <span data-ttu-id="6922c-109">**[各サブスクライバーが Web サーバーに接続する方法を指定します。]**</span><span class="sxs-lookup"><span data-stu-id="6922c-109">**How will each Subscriber connect to the Web server?**</span></span>  
 <span data-ttu-id="6922c-110">Web サーバーへの接続に使用される認証の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="6922c-110">Specify the type of authentication used to connect to the Web server.</span></span> <span data-ttu-id="6922c-111">IIS サーバーへの接続用の [基本認証] を SSL (Secure Sockets Layer) と組み合わせて使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6922c-111">It is recommended to use Basic Authentication for connections to the IIS server in conjunction with Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="6922c-112">[基本認証] を選択した場合は、サブスクライバーから IIS サーバーへの接続に使用されるログインとパスワードを入力してください。</span><span class="sxs-lookup"><span data-stu-id="6922c-112">If you select Basic Authentication, enter the login and password that will be used to connect from the Subscriber to the IIS server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6922c-113">参照</span><span class="sxs-lookup"><span data-stu-id="6922c-113">See Also</span></span>  
 <span data-ttu-id="6922c-114">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="6922c-114">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="6922c-115">[プル サブスクリプションのプロパティの表示または変更](view-and-modify-pull-subscription-properties.md) </span><span class="sxs-lookup"><span data-stu-id="6922c-115">[View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md) </span></span>  
 <span data-ttu-id="6922c-116">[Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md) </span><span class="sxs-lookup"><span data-stu-id="6922c-116">[Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md) </span></span>  
 <span data-ttu-id="6922c-117">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="6922c-117">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 [<span data-ttu-id="6922c-118">マージ レプリケーションの Web 同期</span><span class="sxs-lookup"><span data-stu-id="6922c-118">Web Synchronization for Merge Replication</span></span>](web-synchronization-for-merge-replication.md)  
  
  

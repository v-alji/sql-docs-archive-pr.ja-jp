---
title: FILESTREAM アクセスのためのファイアウォールの構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- Windows Firewall [Database Engine], FILESTREAM
- FILESTREAM [SQL Server], Windows Firewall
ms.assetid: fc52007f-c26f-4f8e-b9d8-55a7978f4d56
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8b787403fefdd336dd82bf7ccb93cdf21fe5a90d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643987"
---
# <a name="configure-a-firewall-for-filestream-access"></a><span data-ttu-id="a3c24-102">FILESTREAM アクセスのためのファイアウォールの構成</span><span class="sxs-lookup"><span data-stu-id="a3c24-102">Configure a Firewall for FILESTREAM Access</span></span>
  <span data-ttu-id="a3c24-103">ファイアウォールで保護された環境で FILESTREAM を使用するには、クライアントとサーバーの両方で、FILESTREAM ファイルが格納されているサーバーの DNS 名を解決できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3c24-103">To use FILESTREAM in a firewall-protected environment, both the client and server must be able to resolve DNS names to the server that contains the FILESTREAM files.</span></span> <span data-ttu-id="a3c24-104">FILESTREAM を使用する場合は、Windows ファイル共有ポート 139 および 445 を開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3c24-104">FILESTREAM requires the Windows file-sharing ports 139 and 445 to be open.</span></span>  
  
### <a name="to-open-the-windows-file-sharing-ports-on-a-computer-that-is-running-windows-7"></a><span data-ttu-id="a3c24-105">Windows 7 を実行しているコンピューターで Windows ファイル共有ポートを開くには</span><span class="sxs-lookup"><span data-stu-id="a3c24-105">To open the Windows file-sharing ports on a computer that is running Windows 7</span></span>  
  
1.  <span data-ttu-id="a3c24-106">コントロール パネルで、 **[Windows ファイアウォール]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="a3c24-106">In Control Panel, open **Windows Firewall**.</span></span>  
  
2.  <span data-ttu-id="a3c24-107">左側のペインの **[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3c24-107">In the left pane, click **Advanced settings**.</span></span> <span data-ttu-id="a3c24-108">管理者パスワードまたは確認を求められたら、パスワードを入力するか、確認を行います。</span><span class="sxs-lookup"><span data-stu-id="a3c24-108">If you're prompted for an administrator password or confirmation, type the password or provide confirmation.</span></span>  
  
3.  <span data-ttu-id="a3c24-109">**[セキュリティが強化された Windows ファイアウォール]** ダイアログ ボックスの左ペインの **[受信の規則]** をクリックした後、右ペインの **[新しい規則]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3c24-109">In the **Windows Firewall with Advanced Security** dialog box, in the left pane, click **Inbound Rules**, and then, in the right pane, click **New Rule**.</span></span>  
  
4.  <span data-ttu-id="a3c24-110">新規の受信の規則のウィザードに従って、TCP ポート 139 を追加します。</span><span class="sxs-lookup"><span data-stu-id="a3c24-110">Follow the instructions in the New Inbound Rule wizard to add TCP port 139.</span></span>  
  
5.  <span data-ttu-id="a3c24-111">前の手順をもう一度実行して、TCP ポート 445 を追加します。</span><span class="sxs-lookup"><span data-stu-id="a3c24-111">Repeat the previous step to add TCP port 445.</span></span>  
  
6.  <span data-ttu-id="a3c24-112">**[セキュリティが強化された Windows ファイアウォール]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a3c24-112">Close the **Windows Firewall with Advanced Security** dialog box.</span></span>  
  
  

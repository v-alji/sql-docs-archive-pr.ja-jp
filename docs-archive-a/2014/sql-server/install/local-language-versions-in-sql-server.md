---
title: SQL Server のローカル言語版 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 20b99363-0490-4aa3-9a3d-262f827d81e8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 646ffaed1e4b709c2c26030379f0a7f223f221e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713717"
---
# <a name="local-language-versions-in-sql-server"></a><span data-ttu-id="70042-102">SQL Server のローカル言語版</span><span class="sxs-lookup"><span data-stu-id="70042-102">Local Language Versions in SQL Server</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="70042-103">では、Windows オペレーティング システムでサポートされているすべての言語がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="70042-103">supports all languages that are supported by Windows operating systems.</span></span>  
  
## <a name="cross-language-support"></a><span data-ttu-id="70042-104">言語間サポート</span><span class="sxs-lookup"><span data-stu-id="70042-104">Cross-Language Support</span></span>  
  
-   <span data-ttu-id="70042-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の英語版は、オペレーティング システムのすべてのローカライズ版で実行できます。</span><span class="sxs-lookup"><span data-stu-id="70042-105">The English-language version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is supported on all localized versions of operating systems.</span></span>  
  
-   <span data-ttu-id="70042-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカライズ版は、対応する言語にローカライズされたオペレーティング システム、または Windows Multilingual User Interface Pack (MUI) 設定を使用することにより、サポートされているオペレーティング システムの英語版でも実行できます。</span><span class="sxs-lookup"><span data-stu-id="70042-106">Localized versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are supported on localized operating systems with the corresponding language or on English-language versions of supported operating systems by using the Windows Multilingual User Interface Pack (MUI) settings.</span></span> <span data-ttu-id="70042-107">詳しくは、「 [Configure Operating System to Support Localized Versions](../../../2014/sql-server/install/local-language-versions-in-sql-server.md#BK_ConfigureOS)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="70042-107">For more information, see [Configure Operating System to Support Localized Versions](../../../2014/sql-server/install/local-language-versions-in-sql-server.md#BK_ConfigureOS).</span></span>  
  
-   <span data-ttu-id="70042-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカライズ版は、同じ言語のローカライズ版にのみアップグレードでき、英語版にはアップグレードできません。</span><span class="sxs-lookup"><span data-stu-id="70042-108">Localized versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can only be upgraded to localized versions of the same language, and cannot be upgraded to the English-language version.</span></span>  
  
-   <span data-ttu-id="70042-109">また、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカライズ版は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の英語インスタンスとサイド バイ サイドでインストールできます。</span><span class="sxs-lookup"><span data-stu-id="70042-109">Localized versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can also be installed side by side with English-language instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
##  <a name="configure-operating-system-to-support-localized-versions"></a><a name="BK_ConfigureOS"></a> <span data-ttu-id="70042-110">Configure Operating System to Support Localized Versions</span><span class="sxs-lookup"><span data-stu-id="70042-110">Configure Operating System to Support Localized Versions</span></span>  
 <span data-ttu-id="70042-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各言語のバージョンは、Windows Multilingual User Interface Pack (MUI) 設定を使用することにより、サポートされているオペレーティング システムの英語バージョン上でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="70042-111">Localized versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are supported on English-language versions of supported operating systems through the use of Windows Multilingual User Interface Pack (MUI) settings.</span></span>  
  
 <span data-ttu-id="70042-112">ただし、英語以外の MUI 設定を持つ英語オペレーティング システムを実行しているサーバーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカライズ バージョンをインストールする場合は、事前にオペレーティング システムのいくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="70042-112">However, you must verify certain operating system settings before installing a localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a server that is running an English-language operating system with a non-English MUI setting.</span></span> <span data-ttu-id="70042-113">以下のオペレーティング システム設定が、インストールする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ローカライズ バージョンの言語に一致していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="70042-113">You need to verify that the following operating system settings match the language of the localized [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to be installed:</span></span>  
  
-   <span data-ttu-id="70042-114">オペレーティング システムのユーザー インターフェイス設定</span><span class="sxs-lookup"><span data-stu-id="70042-114">The operating system user interface setting</span></span>  
  
-   <span data-ttu-id="70042-115">オペレーティング システムのユーザー ロケール設定</span><span class="sxs-lookup"><span data-stu-id="70042-115">The operating system user locale setting</span></span>  
  
-   <span data-ttu-id="70042-116">システム ロケール設定</span><span class="sxs-lookup"><span data-stu-id="70042-116">The system locale setting</span></span>  
  
 <span data-ttu-id="70042-117">この設定と、インストールする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ローカライズ バージョンの言語が一致しない場合は、以下の手順に従ってオペレーティング システムの設定を正しく指定してください。</span><span class="sxs-lookup"><span data-stu-id="70042-117">If the settings do not match the language of the localized [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to be installed, then use the following procedures to correctly set these operating system settings.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="70042-118">異なる言語バージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを、同じコンピューターにインストールすることはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="70042-118">Installations of different language versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances on the same computer are not supported.</span></span>  
  
#### <a name="to-change-the-operating-system-user-interface-setting"></a><span data-ttu-id="70042-119">オペレーティング システムのユーザー インターフェイス設定を変更するには</span><span class="sxs-lookup"><span data-stu-id="70042-119">To change the operating system user interface setting</span></span>  
  
1.  <span data-ttu-id="70042-120">ローカライズ バージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に一致するオペレーティング システム MUI がインストールされていない場合は、インストールします。</span><span class="sxs-lookup"><span data-stu-id="70042-120">If not already installed, install the operating system MUI that matches your localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="70042-121">コントロール パネルで **[地域と言語のオプション]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="70042-121">In Control Panel, open **Regional and Language Options**.</span></span>  
  
3.  <span data-ttu-id="70042-122">**[言語]** タブで、 **[メニューとダイアログで使われる言語]** ボックスの一覧から言語を選択します。</span><span class="sxs-lookup"><span data-stu-id="70042-122">On the **Languages** tab, for **Language used in menus and dialogs**, select a value from the list.</span></span>  
  
     <span data-ttu-id="70042-123">この設定は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のユーザー インターフェイス言語に影響を及ぼします。したがって、ローカライズ バージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="70042-123">This setting will affect the user interface language of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], so it must match your localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
4.  <span data-ttu-id="70042-124">**[適用]** をクリックして変更を確認し、 **[OK]** をクリックしてウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="70042-124">Click **Apply** to confirm the change, and **OK** to close the window.</span></span>  
  
#### <a name="to-change-the-operating-system-user-locale-setting"></a><span data-ttu-id="70042-125">オペレーティング システムのユーザー ロケール設定を変更するには</span><span class="sxs-lookup"><span data-stu-id="70042-125">To change the operating system user locale setting</span></span>  
  
1.  <span data-ttu-id="70042-126">ローカライズ バージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に一致するオペレーティング システム MUI がインストールされていない場合は、インストールします。</span><span class="sxs-lookup"><span data-stu-id="70042-126">If not already installed, install the operating system MUI that matches your localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="70042-127">コントロール パネルで **[地域と言語のオプション]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="70042-127">In Control Panel, open **Regional and Language Options**.</span></span>  
  
3.  <span data-ttu-id="70042-128">**[地域オプション]** タブの **[使う言語を選び、必要に応じてカスタマイズをクリックして希望する形式を選択してください:]** ボックスで、一覧から言語を選択します。</span><span class="sxs-lookup"><span data-stu-id="70042-128">On the **Regional Options** tab, for **Select an item to match its preferences**, select a value from the list.</span></span>  
  
     <span data-ttu-id="70042-129">この設定は、カルチャに特有なデータの書式に影響を及ぼします。</span><span class="sxs-lookup"><span data-stu-id="70042-129">This setting will affect culture-specific data formatting.</span></span>  
  
4.  <span data-ttu-id="70042-130">**[適用]** をクリックして変更を確認し、 **[OK]** をクリックしてウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="70042-130">Click **Apply** to confirm the change, and **OK** to close the window.</span></span>  
  
#### <a name="to-change-the-system-locale-setting"></a><span data-ttu-id="70042-131">システムのロケール設定を変更するには</span><span class="sxs-lookup"><span data-stu-id="70042-131">To change the system locale setting</span></span>  
  
1.  <span data-ttu-id="70042-132">ローカライズ バージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に一致するオペレーティング システム MUI がインストールされていない場合は、インストールします。</span><span class="sxs-lookup"><span data-stu-id="70042-132">If not already installed, install the operating system MUI that matches your localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="70042-133">コントロール パネルで **[地域と言語のオプション]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="70042-133">In Control Panel, open **Regional and Language Options**.</span></span>  
  
3.  <span data-ttu-id="70042-134">**[詳細設定]** タブの **[使う Unicode 対応でないプログラムの言語バージョンに一致する言語を選んでください]** で、一覧から言語を選択します。</span><span class="sxs-lookup"><span data-stu-id="70042-134">On the **Advanced** tab, for **Select a language to match the language version of the non-Unicode programs you want to use**, select a value from the list.</span></span>  
  
     <span data-ttu-id="70042-135">この設定により、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストールに最適な既定照合順序を選択できるようになります。</span><span class="sxs-lookup"><span data-stu-id="70042-135">This setting will allow [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup to choose the best default collation for your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span>  
  
4.  <span data-ttu-id="70042-136">**[適用]** をクリックして変更を確認し、 **[OK]** をクリックしてウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="70042-136">Click **Apply** to confirm the change, and **OK** to close the window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70042-137">参照</span><span class="sxs-lookup"><span data-stu-id="70042-137">See Also</span></span>  
 <span data-ttu-id="70042-138">[SQL Server 2014 をインストールするためのハードウェアおよびソフトウェアの要件](hardware-and-software-requirements-for-installing-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="70042-138">[Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md) </span></span>  
 [<span data-ttu-id="70042-139">SQL Server 2014 のインストール</span><span class="sxs-lookup"><span data-stu-id="70042-139">Install SQL Server 2014</span></span>](../../database-engine/install-windows/install-sql-server.md)  
  
  

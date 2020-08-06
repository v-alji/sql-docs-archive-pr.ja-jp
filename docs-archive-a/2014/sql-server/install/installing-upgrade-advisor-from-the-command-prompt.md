---
title: コマンドプロンプトからのアップグレードアドバイザーのインストール |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- command prompt [Upgrade Advisor]
- Setup [Upgrade Advisor]
- Upgrade Advisor [SQL Server], installing
ms.assetid: a6841cc2-ca13-4b1c-9343-9e4d54312c3a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b0c5193f0b235b6d37170992d9d7ca9568b1f675
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713725"
---
# <a name="installing-upgrade-advisor-from-the-command-prompt"></a><span data-ttu-id="738b0-102">コマンド プロンプトからのアップグレード アドバイザーのインストール</span><span class="sxs-lookup"><span data-stu-id="738b0-102">Installing Upgrade Advisor from the Command Prompt</span></span>
  <span data-ttu-id="738b0-103">アップグレード アドバイザーをインストールするには、セットアップ ウィザードを使用する方法と、コマンド プロンプトを使用する方法があります。</span><span class="sxs-lookup"><span data-stu-id="738b0-103">You can install Upgrade Advisor either by using the Setup Wizard or from the command prompt.</span></span> <span data-ttu-id="738b0-104">コマンド プロンプトを使用すると、自動インストールを実行できます。</span><span class="sxs-lookup"><span data-stu-id="738b0-104">By using the command prompt you can perform unattended and automated installations.</span></span>  
  
## <a name="installation-syntax"></a><span data-ttu-id="738b0-105">インストールの構文</span><span class="sxs-lookup"><span data-stu-id="738b0-105">Installation Syntax</span></span>  
 <span data-ttu-id="738b0-106">コマンド プロンプトからのアップグレード アドバイザーのインストールに使用する基本構文は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="738b0-106">The basic syntax for installing Upgrade Advisor from the command prompt is as follows:</span></span>  
  
 `SQLUA.msi [options]`  
  
 <span data-ttu-id="738b0-107">次の表では、最も一般的なオプションを示します。</span><span class="sxs-lookup"><span data-stu-id="738b0-107">The following table shows the most common options.</span></span>  
  
|<span data-ttu-id="738b0-108">引数</span><span class="sxs-lookup"><span data-stu-id="738b0-108">Argument</span></span>|<span data-ttu-id="738b0-109">説明</span><span class="sxs-lookup"><span data-stu-id="738b0-109">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="738b0-110">/q [n&#124;b&#124;r&#124;f]</span><span class="sxs-lookup"><span data-stu-id="738b0-110">/q[n&#124;b&#124;r&#124;f]</span></span>|<span data-ttu-id="738b0-111">ユーザー インターフェイス (UI) レベルの設定:</span><span class="sxs-lookup"><span data-stu-id="738b0-111">Sets user interface (UI) level:</span></span><br /><br /> <span data-ttu-id="738b0-112">n = UI なし</span><span class="sxs-lookup"><span data-stu-id="738b0-112">n = no UI</span></span><br /><br /> <span data-ttu-id="738b0-113">b = 基本 UI (進行状況のみ、プロンプトなし)</span><span class="sxs-lookup"><span data-stu-id="738b0-113">b = basic UI (progress only, no prompts)</span></span><br /><br /> <span data-ttu-id="738b0-114">r = 一部 UI (インストール終了時のダイアログ ボックス)</span><span class="sxs-lookup"><span data-stu-id="738b0-114">r = reduced UI (dialog box at the end of installation)</span></span><br /><br /> <span data-ttu-id="738b0-115">f = 完全 UI</span><span class="sxs-lookup"><span data-stu-id="738b0-115">f = full UI</span></span>|  
|<span data-ttu-id="738b0-116">/L</span><span class="sxs-lookup"><span data-stu-id="738b0-116">/L</span></span>|<span data-ttu-id="738b0-117">ログ ファイル オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="738b0-117">Specifies log file options.</span></span> <span data-ttu-id="738b0-118">すべてのメッセージを*log_file_name*に記録するには、 **-L \* v**_log_file_name_を使用します。</span><span class="sxs-lookup"><span data-stu-id="738b0-118">To log all messages to *log_file_name*, use **-L\*v**_log_file_name_.</span></span> <span data-ttu-id="738b0-119">エラーメッセージのみを記録するには、 `-Le` *log_file_name*を使用します。</span><span class="sxs-lookup"><span data-stu-id="738b0-119">To log error messages only, use `-Le`*log_file_name*.</span></span>|  
|<span data-ttu-id="738b0-120">ADDLOCAL = ALL&#124; REMOVE = ALL&#124;REINSTALL = ALL</span><span class="sxs-lookup"><span data-stu-id="738b0-120">ADDLOCAL=ALL&#124; REMOVE=ALL&#124;REINSTALL=ALL</span></span>|<span data-ttu-id="738b0-121">アップグレード アドバイザーのインストール (ADDLOCAL)、削除 (REMOVE)、または再インストール (REINSTALL) を実行するように指定します。</span><span class="sxs-lookup"><span data-stu-id="738b0-121">Specifies to install (ADDLOCAL), remove (REMOVE), or reinstall (REINSTALL) Upgrade Advisor.</span></span>|  
|<span data-ttu-id="738b0-122">UAINSTALLDIR=path</span><span class="sxs-lookup"><span data-stu-id="738b0-122">UAINSTALLDIR=path</span></span>|<span data-ttu-id="738b0-123">アップグレード アドバイザーをパスで指定した場所にインストールします。</span><span class="sxs-lookup"><span data-stu-id="738b0-123">Installs Upgrade Advisor to the location specified by path.</span></span>|  
  
## <a name="installation-examples"></a><span data-ttu-id="738b0-124">インストール例</span><span class="sxs-lookup"><span data-stu-id="738b0-124">Installation Examples</span></span>  
 <span data-ttu-id="738b0-125">次の例は、コマンド プロンプトを使用してアップグレード アドバイザーをインストールする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="738b0-125">The following example shows how to install Upgrade Advisor by using the command prompt:</span></span>  
  
```  
SQLUA.msi /qn ADDLOCAL=ALL UAINSTALLDIR="C:\Upgrade Advisor"  
```  
  
 <span data-ttu-id="738b0-126">このコマンドの実行時に、Msiexec プログラムを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="738b0-126">You can also use the Msiexec program when you run this command:</span></span>  
  
```  
Msiexec.exe /i C:\Downloads\SQLUA.msi /qn ADDLOCAL=ALL UAINSTALLDIR="C:\Upgrade Advisor"  
```  
  
 <span data-ttu-id="738b0-127">これは、追加インストール オプションを使用する必要がある場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="738b0-127">This can be helpful if you have to use additional installation options.</span></span>  
  
## <a name="removal-examples"></a><span data-ttu-id="738b0-128">削除例</span><span class="sxs-lookup"><span data-stu-id="738b0-128">Removal Examples</span></span>  
 <span data-ttu-id="738b0-129">次の例は、コマンド プロンプトを使用してアップグレード アドバイザーを削除する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="738b0-129">The following example shows how to remove Upgrade Advisor by using the command prompt:</span></span>  
  
```  
SQLUA.msi /qn REMOVE=ALL  
```  
  
 <span data-ttu-id="738b0-130">このコマンドの実行時に、Msiexec プログラムを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="738b0-130">You can also use the Msiexec program when you run this command:</span></span>  
  
```  
Msiexec.exe /i C:\Downloads\SQLUA.msi /qn REMOVE=ALL  
```  
  
## <a name="see-also"></a><span data-ttu-id="738b0-131">参照</span><span class="sxs-lookup"><span data-stu-id="738b0-131">See Also</span></span>  
 <span data-ttu-id="738b0-132">[アップグレードアドバイザーをインストールしています](../../../2014/sql-server/install/installing-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="738b0-132">[Installing Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="738b0-133">アップグレード アドバイザーの前提条件</span><span class="sxs-lookup"><span data-stu-id="738b0-133">Upgrade Advisor Prerequisites</span></span>](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)  
  
  

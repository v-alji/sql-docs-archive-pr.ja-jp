---
title: '[パッケージのエクスポート] ダイアログボックスの UI リファレンス |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dtsserver.exportpackage.f1
helpviewer_keywords:
- Export Package dialog box
ms.assetid: 3742fe8a-ef57-444d-b2fb-cb25d16bae97
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8aedb771dc61fca737ba3841e65b8cb8655d173e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743398"
---
# <a name="export-package-dialog-box-ui-reference"></a><span data-ttu-id="dc33c-102">[パッケージのエクスポート] ダイアログ ボックスの UI リファレンス</span><span class="sxs-lookup"><span data-stu-id="dc33c-102">Export Package Dialog Box UI Reference</span></span>
  <span data-ttu-id="dc33c-103">**の** [パッケージのエクスポート] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]ダイアログ ボックスを使用すると、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを別の場所にエクスポートしたり、必要に応じてパッケージの保護レベルを変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="dc33c-103">Use the **Export Package** dialog box, available in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], to export a [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package to a different location and optionally, modify the protection level of the package.</span></span>  
  
## <a name="options"></a><span data-ttu-id="dc33c-104">オプション</span><span class="sxs-lookup"><span data-stu-id="dc33c-104">Options</span></span>  
 <span data-ttu-id="dc33c-105">**[パッケージの場所]**</span><span class="sxs-lookup"><span data-stu-id="dc33c-105">**Package location**</span></span>  
 <span data-ttu-id="dc33c-106">パッケージをエクスポートする格納場所の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc33c-106">Select the type of storage to export the package to.</span></span> <span data-ttu-id="dc33c-107">次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="dc33c-107">The following options are available:</span></span>  
  
 <span data-ttu-id="dc33c-108">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="dc33c-108">**SQL Server**</span></span>  
  
 <span data-ttu-id="dc33c-109">**ファイル システム**</span><span class="sxs-lookup"><span data-stu-id="dc33c-109">**File System**</span></span>  
  
 <span data-ttu-id="dc33c-110">**[SSIS パッケージ ストア]**</span><span class="sxs-lookup"><span data-stu-id="dc33c-110">**SSIS Package Storage**</span></span>  
  
 <span data-ttu-id="dc33c-111">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="dc33c-111">**Server**</span></span>  
 <span data-ttu-id="dc33c-112">サーバー名を入力するか、サーバーを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="dc33c-112">Type a server name or select a server from the list.</span></span>  
  
 <span data-ttu-id="dc33c-113">**認証**</span><span class="sxs-lookup"><span data-stu-id="dc33c-113">**Authentication**</span></span>  
 <span data-ttu-id="dc33c-114">Windows 認証または [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc33c-114">Select Windows Authentication or [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="dc33c-115">このオプションは、格納場所が [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の場合のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="dc33c-115">This option is available only if the storage location is [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="dc33c-116">可能であれば、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="dc33c-116">Whenever possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="dc33c-117">**認証の種類**</span><span class="sxs-lookup"><span data-stu-id="dc33c-117">**Authentication type**</span></span>  
 <span data-ttu-id="dc33c-118">認証の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc33c-118">Select an authentication type.</span></span>  
  
 <span data-ttu-id="dc33c-119">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="dc33c-119">**User name**</span></span>  
 <span data-ttu-id="dc33c-120">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用する場合は、ユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="dc33c-120">If using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a user name.</span></span>  
  
 <span data-ttu-id="dc33c-121">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="dc33c-121">**Password**</span></span>  
 <span data-ttu-id="dc33c-122">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用する場合は、パスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="dc33c-122">If using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a password.</span></span>  
  
 <span data-ttu-id="dc33c-123">**[パッケージのパス]**</span><span class="sxs-lookup"><span data-stu-id="dc33c-123">**Package path**</span></span>  
 <span data-ttu-id="dc33c-124">パッケージのパスを入力するか、参照ボタン **[...]** をクリックしてパッケージを格納するフォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="dc33c-124">Type the package path, or click the browse button **(...)** and locate the folder in which to store the package.</span></span>  
  
 <span data-ttu-id="dc33c-125">**保護レベル**</span><span class="sxs-lookup"><span data-stu-id="dc33c-125">**Protection level**</span></span>  
 <span data-ttu-id="dc33c-126">参照ボタン **[...]** をクリックして、 **[パッケージの保護レベル]** ダイアログ ボックスで保護レベルを更新します。</span><span class="sxs-lookup"><span data-stu-id="dc33c-126">Click the browse button **(...)** and update the protection level in the **Package Protection Level** dialog box.</span></span> <span data-ttu-id="dc33c-127">詳細については、「 [[パッケージの保護レベル] ダイアログ ボックス](../../2014/integration-services/package-and-project-protection-level-dialog-box.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc33c-127">For more information, see [Package and Project Protection Level Dialog Box](../../2014/integration-services/package-and-project-protection-level-dialog-box.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc33c-128">参照</span><span class="sxs-lookup"><span data-stu-id="dc33c-128">See Also</span></span>  
 <span data-ttu-id="dc33c-129">[パッケージのコピーの保存](../../2014/integration-services/save-copy-of-package.md) </span><span class="sxs-lookup"><span data-stu-id="dc33c-129">[Save Copy of Package](../../2014/integration-services/save-copy-of-package.md) </span></span>  
 <span data-ttu-id="dc33c-130">[[パッケージのインポート] ダイアログボックスの UI リファレンス](../../2014/integration-services/import-package-dialog-box-ui-reference.md) </span><span class="sxs-lookup"><span data-stu-id="dc33c-130">[Import Package Dialog Box UI Reference](../../2014/integration-services/import-package-dialog-box-ui-reference.md) </span></span>  
 <span data-ttu-id="dc33c-131">[パッケージの保存](save-packages.md) </span><span class="sxs-lookup"><span data-stu-id="dc33c-131">[Save Packages](save-packages.md) </span></span>  
 [<span data-ttu-id="dc33c-132">パッケージをインポートおよびエクスポートする &#40;SSIS サービス&#41;</span><span class="sxs-lookup"><span data-stu-id="dc33c-132">Import and Export Packages &#40;SSIS Service&#41;</span></span>](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  

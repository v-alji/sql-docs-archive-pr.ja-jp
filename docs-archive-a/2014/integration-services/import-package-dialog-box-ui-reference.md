---
title: '[パッケージのインポート] ダイアログボックスの UI リファレンス |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dtsserver.importpackage.f1
helpviewer_keywords:
- Import Package dialog box
ms.assetid: 0e5fb127-c7ff-4dfa-b90e-d9bcf0ce763b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ff20bf8eb221778465a26944280d53b6aab07601
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641157"
---
# <a name="import-package-dialog-box-ui-reference"></a><span data-ttu-id="ffcce-102">[パッケージのインポート] ダイアログ ボックスの UI リファレンス</span><span class="sxs-lookup"><span data-stu-id="ffcce-102">Import Package Dialog Box UI Reference</span></span>
  <span data-ttu-id="ffcce-103">**の** [パッケージのインポート] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]ダイアログ ボックスを使用すると、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージをインポートしたり、パッケージの保護レベルの設定や変更を行ったりできます。</span><span class="sxs-lookup"><span data-stu-id="ffcce-103">Use the **Import Package** dialog box, available in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], to import a [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package and to set or modify the protection level of the package.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ffcce-104">オプション</span><span class="sxs-lookup"><span data-stu-id="ffcce-104">Options</span></span>  
 <span data-ttu-id="ffcce-105">**[パッケージの場所]**</span><span class="sxs-lookup"><span data-stu-id="ffcce-105">**Package location**</span></span>  
 <span data-ttu-id="ffcce-106">パッケージをインポートする格納場所の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="ffcce-106">Select the type of storage location to import the package to.</span></span> <span data-ttu-id="ffcce-107">次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ffcce-107">The following options are available:</span></span>  
  
 <span data-ttu-id="ffcce-108">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="ffcce-108">**SQL Server**</span></span>  
  
 <span data-ttu-id="ffcce-109">**ファイル システム**</span><span class="sxs-lookup"><span data-stu-id="ffcce-109">**File System**</span></span>  
  
 <span data-ttu-id="ffcce-110">**[SSIS パッケージ ストア]**</span><span class="sxs-lookup"><span data-stu-id="ffcce-110">**SSIS Package Store**</span></span>  
  
 <span data-ttu-id="ffcce-111">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="ffcce-111">**Server**</span></span>  
 <span data-ttu-id="ffcce-112">サーバー名を入力するか、サーバーを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="ffcce-112">Type a server name or select a server from the list.</span></span>  
  
 <span data-ttu-id="ffcce-113">**認証**</span><span class="sxs-lookup"><span data-stu-id="ffcce-113">**Authentication**</span></span>  
 <span data-ttu-id="ffcce-114">Windows 認証または [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を選択します。</span><span class="sxs-lookup"><span data-stu-id="ffcce-114">Select Windows Authentication or [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="ffcce-115">このオプションは、格納場所が [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の場合のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ffcce-115">This option is available only if the storage location is [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ffcce-116">可能であれば、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="ffcce-116">Whenever possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="ffcce-117">**認証の種類**</span><span class="sxs-lookup"><span data-stu-id="ffcce-117">**Authentication type**</span></span>  
 <span data-ttu-id="ffcce-118">認証の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="ffcce-118">Select an authentication type.</span></span>  
  
 <span data-ttu-id="ffcce-119">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="ffcce-119">**User name**</span></span>  
 <span data-ttu-id="ffcce-120">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用する場合は、ユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="ffcce-120">If using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a user name.</span></span>  
  
 <span data-ttu-id="ffcce-121">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="ffcce-121">**Password**</span></span>  
 <span data-ttu-id="ffcce-122">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用する場合は、パスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="ffcce-122">If using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a password.</span></span>  
  
 <span data-ttu-id="ffcce-123">**[パッケージのパス]**</span><span class="sxs-lookup"><span data-stu-id="ffcce-123">**Package path**</span></span>  
 <span data-ttu-id="ffcce-124">パッケージのパスを入力するか、参照ボタン **[...]** をクリックしてパッケージを指定します。</span><span class="sxs-lookup"><span data-stu-id="ffcce-124">Type the package path, or click the browse button **(...)** and locate the package.</span></span>  
  
 <span data-ttu-id="ffcce-125">**パッケージ名**</span><span class="sxs-lookup"><span data-stu-id="ffcce-125">**Package name**</span></span>  
 <span data-ttu-id="ffcce-126">オプションでパッケージの名前を変更できます。</span><span class="sxs-lookup"><span data-stu-id="ffcce-126">Optionally, rename the package.</span></span> <span data-ttu-id="ffcce-127">既定の名前は、インポートするパッケージの名前です。</span><span class="sxs-lookup"><span data-stu-id="ffcce-127">The default name is the name of the package to import.</span></span>  
  
 <span data-ttu-id="ffcce-128">**保護レベル**</span><span class="sxs-lookup"><span data-stu-id="ffcce-128">**Protection level**</span></span>  
 <span data-ttu-id="ffcce-129">参照ボタン **[...]** をクリックし、 **[パッケージの保護レベル]** ダイアログ ボックスで保護レベルを更新します。</span><span class="sxs-lookup"><span data-stu-id="ffcce-129">Click the browse button **(...)** and, in the **Package Protection Level** dialog box, update the protection level.</span></span> <span data-ttu-id="ffcce-130">詳細については、「 [[パッケージの保護レベル] ダイアログ ボックス](../../2014/integration-services/package-and-project-protection-level-dialog-box.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffcce-130">For more information, see [Package and Project Protection Level Dialog Box](../../2014/integration-services/package-and-project-protection-level-dialog-box.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffcce-131">参照</span><span class="sxs-lookup"><span data-stu-id="ffcce-131">See Also</span></span>  
 <span data-ttu-id="ffcce-132">[パッケージのコピーの保存](../../2014/integration-services/save-copy-of-package.md) </span><span class="sxs-lookup"><span data-stu-id="ffcce-132">[Save Copy of Package](../../2014/integration-services/save-copy-of-package.md) </span></span>  
 <span data-ttu-id="ffcce-133">[[パッケージのエクスポート] ダイアログボックスの UI リファレンス](../../2014/integration-services/export-package-dialog-box-ui-reference.md) </span><span class="sxs-lookup"><span data-stu-id="ffcce-133">[Export Package Dialog Box UI Reference](../../2014/integration-services/export-package-dialog-box-ui-reference.md) </span></span>  
 <span data-ttu-id="ffcce-134">[パッケージの保存](save-packages.md) </span><span class="sxs-lookup"><span data-stu-id="ffcce-134">[Save Packages](save-packages.md) </span></span>  
 [<span data-ttu-id="ffcce-135">パッケージをインポートおよびエクスポートする &#40;SSIS サービス&#41;</span><span class="sxs-lookup"><span data-stu-id="ffcce-135">Import and Export Packages &#40;SSIS Service&#41;</span></span>](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  

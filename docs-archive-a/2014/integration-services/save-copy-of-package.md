---
title: パッケージのコピーを保存する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.savecopyas.f1
helpviewer_keywords:
- Save Copy of Package dialog box
ms.assetid: 7b44c0d7-d8fa-4491-8836-0899f621d3a8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f0a685d8b38299e1ba1d03c4ec8c1052cc957dbb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738515"
---
# <a name="save-copy-of-package"></a><span data-ttu-id="0a977-102">[パッケージのコピーの保存]</span><span class="sxs-lookup"><span data-stu-id="0a977-102">Save Copy of Package</span></span>
  <span data-ttu-id="0a977-103">**の** [パッケージのコピーの保存] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]ダイアログ ボックスを使用すると、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージのコピーを [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] から別の場所に保存し、必要に応じてパッケージの保護レベルを変更できます。</span><span class="sxs-lookup"><span data-stu-id="0a977-103">Use the **Save Copy of Package** dialog box, available in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], to save a copy of an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package from [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to a different location and, optionally, modify the protection level of the package.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0a977-104">オプション</span><span class="sxs-lookup"><span data-stu-id="0a977-104">Options</span></span>  
 <span data-ttu-id="0a977-105">**[パッケージの場所]**</span><span class="sxs-lookup"><span data-stu-id="0a977-105">**Package location**</span></span>  
 <span data-ttu-id="0a977-106">パッケージ コピーを保存する格納場所の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a977-106">Select the type of storage location in which to save the package copy.</span></span> <span data-ttu-id="0a977-107">次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0a977-107">The following options are available:</span></span>  
  
 <span data-ttu-id="0a977-108">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="0a977-108">**SQL Server**</span></span>  
  
 <span data-ttu-id="0a977-109">**ファイル システム**</span><span class="sxs-lookup"><span data-stu-id="0a977-109">**File System**</span></span>  
  
 <span data-ttu-id="0a977-110">**[SSIS パッケージ ストア]**</span><span class="sxs-lookup"><span data-stu-id="0a977-110">**SSIS Package Store**</span></span>  
  
 <span data-ttu-id="0a977-111">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="0a977-111">**Server**</span></span>  
 <span data-ttu-id="0a977-112">サーバー名を入力するか、サーバーを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="0a977-112">Type a server name or select a server from the list.</span></span> <span data-ttu-id="0a977-113">このオプションは、格納場所が **[SQL Server]** または **[SSIS パッケージ ストア]** の場合のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="0a977-113">This option is available only if the storage location is **SQL Server** or **SSIS Package Store**.</span></span>  
  
 <span data-ttu-id="0a977-114">**認証**</span><span class="sxs-lookup"><span data-stu-id="0a977-114">**Authentication**</span></span>  
 <span data-ttu-id="0a977-115">Windows 認証または [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a977-115">Select Windows Authentication or [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="0a977-116">このオプションは、格納場所が [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の場合のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="0a977-116">This option is available only if the storage location is [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0a977-117">可能であれば、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="0a977-117">Whenever possible use Windows Authentication.</span></span>  
  
 <span data-ttu-id="0a977-118">**認証の種類**</span><span class="sxs-lookup"><span data-stu-id="0a977-118">**Authentication type**</span></span>  
 <span data-ttu-id="0a977-119">認証の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a977-119">Select an authentication type.</span></span>  
  
 <span data-ttu-id="0a977-120">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="0a977-120">**User name**</span></span>  
 <span data-ttu-id="0a977-121">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用する場合は、ユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="0a977-121">If using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a user name.</span></span>  
  
 <span data-ttu-id="0a977-122">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="0a977-122">**Password**</span></span>  
 <span data-ttu-id="0a977-123">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用する場合は、パスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="0a977-123">If using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a password.</span></span>  
  
 <span data-ttu-id="0a977-124">**[パッケージのパス]**</span><span class="sxs-lookup"><span data-stu-id="0a977-124">**Package path**</span></span>  
 <span data-ttu-id="0a977-125">パッケージのパスを入力するか、参照ボタン **([..** .]) をクリックして、パッケージを保存するフォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="0a977-125">Type the package path, or click the browse **(...)** button and locate the folder in which to store the package.</span></span>  
  
 <span data-ttu-id="0a977-126">**保護レベル**</span><span class="sxs-lookup"><span data-stu-id="0a977-126">**Protection level**</span></span>  
 <span data-ttu-id="0a977-127">参照ボタン **([..** .]) をクリックし、[パッケージの**保護レベル**] ダイアログボックスで保護レベルを更新します。</span><span class="sxs-lookup"><span data-stu-id="0a977-127">Click the browse **(...)** button and update the protection level in the **Package Protection Level** dialog box.</span></span> <span data-ttu-id="0a977-128">詳細については、「 [[パッケージの保護レベル] ダイアログ ボックス](../../2014/integration-services/package-and-project-protection-level-dialog-box.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a977-128">For more information, see [Package and Project Protection Level Dialog Box](../../2014/integration-services/package-and-project-protection-level-dialog-box.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a977-129">参照</span><span class="sxs-lookup"><span data-stu-id="0a977-129">See Also</span></span>  
 <span data-ttu-id="0a977-130">[[パッケージのインポート] ダイアログボックスの UI リファレンス](../../2014/integration-services/import-package-dialog-box-ui-reference.md) </span><span class="sxs-lookup"><span data-stu-id="0a977-130">[Import Package Dialog Box UI Reference](../../2014/integration-services/import-package-dialog-box-ui-reference.md) </span></span>  
 <span data-ttu-id="0a977-131">[[パッケージのエクスポート] ダイアログボックスの UI リファレンス](../../2014/integration-services/export-package-dialog-box-ui-reference.md) </span><span class="sxs-lookup"><span data-stu-id="0a977-131">[Export Package Dialog Box UI Reference](../../2014/integration-services/export-package-dialog-box-ui-reference.md) </span></span>  
 <span data-ttu-id="0a977-132">[パッケージの保存](save-packages.md) </span><span class="sxs-lookup"><span data-stu-id="0a977-132">[Save Packages](save-packages.md) </span></span>  
 [<span data-ttu-id="0a977-133">パッケージをインポートおよびエクスポートする &#40;SSIS サービス&#41;</span><span class="sxs-lookup"><span data-stu-id="0a977-133">Import and Export Packages &#40;SSIS Service&#41;</span></span>](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  

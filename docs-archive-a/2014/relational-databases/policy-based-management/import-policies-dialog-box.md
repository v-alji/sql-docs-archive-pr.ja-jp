---
title: '[ポリシーのインポート] ダイアログ ボックス | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.importpolicy.f1
ms.assetid: 78ab5f6e-2f13-4788-937e-8892ef4e2345
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2601c21ea08d00bf77e9b97a5186f2d6d1200a10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632439"
---
# <a name="import-policies-dialog-box"></a><span data-ttu-id="3945e-102">[ポリシーのインポート] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="3945e-102">Import Policies Dialog Box</span></span>
  <span data-ttu-id="3945e-103">このダイアログ ボックスを使用すると、XML ファイルとして保存された 1 つ以上のポリシー (およびその参照された条件) を [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] の現在のインスタンスにインポートできます。</span><span class="sxs-lookup"><span data-stu-id="3945e-103">Use this dialog box to import one or more policies (and their referenced condition) that are saved as XML files, into the current [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] instance.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3945e-104">オプション</span><span class="sxs-lookup"><span data-stu-id="3945e-104">Options</span></span>  
 <span data-ttu-id="3945e-105">**[インポートするファイル]**</span><span class="sxs-lookup"><span data-stu-id="3945e-105">**Files to import**</span></span>  
 <span data-ttu-id="3945e-106">XML ファイルからポリシーをインポートするには、ファイルのパスと名前を入力するか、参照ボタン ( **[...]** ) を使用します。</span><span class="sxs-lookup"><span data-stu-id="3945e-106">To import a policy from an XML file, type the path and name of the file or use the Browse (**...**) button.</span></span>  
  
 <span data-ttu-id="3945e-107">**[インポートされるアイテムと重複部分を置き換える]**</span><span class="sxs-lookup"><span data-stu-id="3945e-107">**Replace duplicates with items imported**</span></span>  
 <span data-ttu-id="3945e-108">この [!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスに同じ名前のポリシーまたは条件が既に存在する場合、その既存のポリシーまたは条件が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="3945e-108">Select to overwrite any existing policy or condition of the same name if it already exists on this [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance.</span></span> <span data-ttu-id="3945e-109">依存ポリシーを使用している条件は、依存ポリシーも上書きしない限り上書きできません。</span><span class="sxs-lookup"><span data-stu-id="3945e-109">A condition with a dependent policy cannot be overwritten unless the dependent policy is also being overwritten.</span></span> <span data-ttu-id="3945e-110">このオプションを選択していない場合は、同じ条件式を使用している既存の条件によってエラーが発生することはありません。</span><span class="sxs-lookup"><span data-stu-id="3945e-110">If this option is not selected, an existing condition that is using the same condition expression will not cause an error.</span></span>  
  
 <span data-ttu-id="3945e-111">**[ポリシーの状態]**</span><span class="sxs-lookup"><span data-stu-id="3945e-111">**Policy state**</span></span>  
 <span data-ttu-id="3945e-112">インポートしたポリシーの状態を選択します。</span><span class="sxs-lookup"><span data-stu-id="3945e-112">Select the state that you want for the imported policy:</span></span>  
  
-   <span data-ttu-id="3945e-113">**[インポート時にポリシーの状態を保存します]**</span><span class="sxs-lookup"><span data-stu-id="3945e-113">**Preserve policy state on import**</span></span>  
  
-   <span data-ttu-id="3945e-114">**[インポート時にすべてのポリシーを有効にします]**</span><span class="sxs-lookup"><span data-stu-id="3945e-114">**Enable all policies on import**</span></span>  
  
-   <span data-ttu-id="3945e-115">**[インポート時にすべてのポリシーを無効にします]**</span><span class="sxs-lookup"><span data-stu-id="3945e-115">**Disable all policies on import**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3945e-116">参照</span><span class="sxs-lookup"><span data-stu-id="3945e-116">See Also</span></span>  
 <span data-ttu-id="3945e-117">[ポリシー ベースの管理を使用したサーバーの管理](administer-servers-by-using-policy-based-management.md) </span><span class="sxs-lookup"><span data-stu-id="3945e-117">[Administer Servers by Using Policy-Based Management](administer-servers-by-using-policy-based-management.md) </span></span>  
 <span data-ttu-id="3945e-118">[ポリシー ベースの管理ポリシーのインポート](import-a-policy-based-management-policy.md) </span><span class="sxs-lookup"><span data-stu-id="3945e-118">[Import a Policy-Based Management Policy](import-a-policy-based-management-policy.md) </span></span>  
 [<span data-ttu-id="3945e-119">ポリシーベースの管理ポリシーのエクスポート</span><span class="sxs-lookup"><span data-stu-id="3945e-119">Export a Policy-Based Management Policy</span></span>](export-a-policy-based-management-policy.md)  
  
  

---
title: Lock Pages in Memory オプションの有効化 (Windows) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Lock Pages in Memory option
ms.assetid: cd581fbc-4747-439e-87f9-2f18e39c5bb9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 13290940c3a94a7ba79582d892a5e28670f24b29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641236"
---
# <a name="enable-the-lock-pages-in-memory-option-windows"></a><span data-ttu-id="a7d0d-102">Lock Pages in Memory オプションの有効化 (Windows)</span><span class="sxs-lookup"><span data-stu-id="a7d0d-102">Enable the Lock Pages in Memory Option (Windows)</span></span>
  <span data-ttu-id="a7d0d-103">この Windows ポリシーにより、プロセスを使用して物理メモリにデータを保持できるアカウントを指定し、ディスク上の仮想メモリへのデータのページングを防止します。</span><span class="sxs-lookup"><span data-stu-id="a7d0d-103">This Windows policy determines which accounts can use a process to keep data in physical memory, preventing the system from paging the data to virtual memory on disk.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a7d0d-104">メモリ内のページをロックすると、ディスクへのメモリのページングの際にパフォーマンスが向上する場合があります。</span><span class="sxs-lookup"><span data-stu-id="a7d0d-104">Locking pages in memory may boost performance when paging memory to disk is expected.</span></span>  
  
 <span data-ttu-id="a7d0d-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が使用するアカウントに対してこのポリシーを有効にするには、Windows グループ ポリシー ツール (gpedit.msc) を使用します。</span><span class="sxs-lookup"><span data-stu-id="a7d0d-105">Use the Windows Group Policy tool (gpedit.msc) to enable this policy for the account used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a7d0d-106">このポリシーを変更できるのは、システム管理者だけです。</span><span class="sxs-lookup"><span data-stu-id="a7d0d-106">You must be a system administrator to change this policy.</span></span>  
  
### <a name="to-enable-the-lock-pages-in-memory-option"></a><span data-ttu-id="a7d0d-107">lock pages in memory オプションを有効にするには</span><span class="sxs-lookup"><span data-stu-id="a7d0d-107">To enable the lock pages in memory option</span></span>  
  
1.  <span data-ttu-id="a7d0d-108">**[スタート]** メニューの **[ファイル名を指定して実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7d0d-108">On the **Start** menu, click **Run**.</span></span> <span data-ttu-id="a7d0d-109">[**名前**] ボックスに「」と入力 `gpedit.msc` します。</span><span class="sxs-lookup"><span data-stu-id="a7d0d-109">In the **Open** box, type `gpedit.msc`.</span></span>  
  
2.  <span data-ttu-id="a7d0d-110">**[ローカル グループ ポリシー エディター]** コンソールで **[コンピューターの構成]** を展開し、次に **[Windows の設定]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="a7d0d-110">On the **Local Group Policy Editor** console, expand **Computer Configuration**, and then expand **Windows Settings**.</span></span>  
  
3.  <span data-ttu-id="a7d0d-111">**[セキュリティの設定]** を展開し、 **[ローカル ポリシー]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="a7d0d-111">Expand **Security Settings**, and then expand **Local Policies**.</span></span>  
  
4.  <span data-ttu-id="a7d0d-112">**[ユーザー権利の割り当て]** フォルダーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7d0d-112">Select the **User Rights Assignment** folder.</span></span>  
  
     <span data-ttu-id="a7d0d-113">ポリシーが詳細ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7d0d-113">The policies will be displayed in the details pane.</span></span>  
  
5.  <span data-ttu-id="a7d0d-114">詳細ペインで、 **[メモリ内のページのロック]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7d0d-114">In the pane, double-click **Lock pages in memory**.</span></span>  
  
6.  <span data-ttu-id="a7d0d-115">**[ローカル セキュリティの設定 - メモリ内のページのロック]** ダイアログ ボックスで、 **[ユーザーまたはグループの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7d0d-115">In the **Local Security Setting - Lock pages in memory** dialog box, click **Add User or Group**.</span></span>  
  
7.  <span data-ttu-id="a7d0d-116">**[ユーザー、サービス アカウント、またはグループの選択]** ダイアログ ボックスで、sqlservr.exe の実行権限のあるアカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="a7d0d-116">In the **Select Users, Service Accounts, or Groups** dialog box, add an account with privileges to run sqlservr.exe.</span></span>  
  
8.  <span data-ttu-id="a7d0d-117">この変更を有効にするには、ログアウトして、再びログインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7d0d-117">Log out and then log back in for this change to take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7d0d-118">参照</span><span class="sxs-lookup"><span data-stu-id="a7d0d-118">See Also</span></span>  
 [<span data-ttu-id="a7d0d-119">サーバー メモリに関するサーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="a7d0d-119">Server Memory Server Configuration Options</span></span>](server-memory-server-configuration-options.md)  
  
  

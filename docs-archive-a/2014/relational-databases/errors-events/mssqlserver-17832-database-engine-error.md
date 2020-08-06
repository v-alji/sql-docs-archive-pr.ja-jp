---
title: MSSQLSERVER_17832 | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17828 (Database Engine error)
- maxtokensize
- 17832 (Database Engine error)
- login packet (bad)
ms.assetid: bd56ffe4-0855-4ada-8aca-251fbc6ff2ce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dba214e2cce04ff2583e12ae7cee9b54373390a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713222"
---
# <a name="mssqlserver_17832"></a><span data-ttu-id="3b0f5-102">MSSQLSERVER_17832</span><span class="sxs-lookup"><span data-stu-id="3b0f5-102">MSSQLSERVER_17832</span></span>
    
## <a name="details"></a><span data-ttu-id="3b0f5-103">詳細</span><span class="sxs-lookup"><span data-stu-id="3b0f5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3b0f5-104">製品名</span><span class="sxs-lookup"><span data-stu-id="3b0f5-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="3b0f5-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3b0f5-105">Event ID</span></span>|<span data-ttu-id="3b0f5-106">17832</span><span class="sxs-lookup"><span data-stu-id="3b0f5-106">17832</span></span>|  
|<span data-ttu-id="3b0f5-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="3b0f5-107">Event Source</span></span>|<span data-ttu-id="3b0f5-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="3b0f5-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="3b0f5-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="3b0f5-109">Component</span></span>|<span data-ttu-id="3b0f5-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="3b0f5-110">SQLEngine</span></span>|  
|<span data-ttu-id="3b0f5-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="3b0f5-111">Symbolic Name</span></span>|<span data-ttu-id="3b0f5-112">SRV_BAD_LOGIN_PKT</span><span class="sxs-lookup"><span data-stu-id="3b0f5-112">SRV_BAD_LOGIN_PKT</span></span>|  
|<span data-ttu-id="3b0f5-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="3b0f5-113">Message Text</span></span>|<span data-ttu-id="3b0f5-114">接続を開くのに使用したログイン パケットの構造は無効です。接続が閉じられました。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-114">The login packet used to open the connection is structurally invalid; the connection has been closed.</span></span> <span data-ttu-id="3b0f5-115">クライアント ライブラリのベンダーに問い合わせてください。%.\*ls</span><span class="sxs-lookup"><span data-stu-id="3b0f5-115">Please contact the vendor of the client library.%.\*ls</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3b0f5-116">説明</span><span class="sxs-lookup"><span data-stu-id="3b0f5-116">Explanation</span></span>  
 <span data-ttu-id="3b0f5-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターはクライアントのログイン パケットを処理できませんでした。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-117">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer was unable to process the client login packet.</span></span> <span data-ttu-id="3b0f5-118">パケットが正しく作成されなかったか、パケットが転送中に破損した可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-118">This may be because the packet was created improperly or because the packet was damaged during transmission.</span></span> <span data-ttu-id="3b0f5-119">また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターの構成が原因である可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-119">It can also be caused by the configuration of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer.</span></span> <span data-ttu-id="3b0f5-120">表示される IP アドレスは、クライアント コンピューターのアドレスです。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-120">The IP address listed is the address of the client computer.</span></span>  
  
### <a name="more-information"></a><span data-ttu-id="3b0f5-121">詳細情報</span><span class="sxs-lookup"><span data-stu-id="3b0f5-121">More Information</span></span>  
 <span data-ttu-id="3b0f5-122">Kerberos 環境で Windows 認証を使用する場合、クライアントは特権属性証明 (PAC) を含む Kerberos チケットを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-122">When using Windows Authentication in a Kerberos environment, a client receives a Kerberos ticket that contains a Privilege Attribute Certificate (PAC).</span></span> <span data-ttu-id="3b0f5-123">PAC には、ユーザーがメンバーとなっているグループ、ユーザーが持つ権限、ユーザーに適用されるポリシーなど、さまざまな種類の承認データが含まれます。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-123">The PAC contains various types of authorization data including groups that the user is a member of, rights the user has, and what policies apply to the user.</span></span> <span data-ttu-id="3b0f5-124">クライアントが Kerberos チケットを受け取ると、PAC に含まれる情報を使用してユーザーのアクセス トークンが生成されます。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-124">When the client receives the Kerberos ticket, the information contained in the PAC is used to generate the user's access token.</span></span> <span data-ttu-id="3b0f5-125">クライアントは、このトークンをログイン パケットの一部として [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターに提供します。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-125">The client presents the token to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer as part of the login packet.</span></span>  
  
 <span data-ttu-id="3b0f5-126">トークンが正しく作成されなかったか、転送中に破損した場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は問題に関する追加情報を提供できません。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-126">If the token was improperly created or damaged during transmission, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot offer additional information about the problem.</span></span>  
  
 <span data-ttu-id="3b0f5-127">ユーザーが多数のグループのメンバーであるか、多数のポリシーを持つ場合、それらすべてを一覧表示するトークンは通常よりも大きくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-127">When the user is a member of many groups or has many policies, the token may grow larger than normal to list them all.</span></span> <span data-ttu-id="3b0f5-128">トークンがサーバー コンピューターの **MaxTokenSize** 値よりも大きくなると、クライアントは一般的なネットワーク エラー (GNE) によって接続に失敗し、エラー 17832 が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-128">If the token grows larger than the **MaxTokenSize** value of the server computer, the client fails to connect with a General Network Error (GNE) and error 17832 can occur.</span></span> <span data-ttu-id="3b0f5-129">この問題は、多数のグループに属しているか、多数のポリシーを持つ一部のユーザーのみに影響します。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-129">This problem may affect only some users: users with many groups or policies.</span></span> <span data-ttu-id="3b0f5-130">問題の原因がサーバー コンピューターの **MaxTokenSize** 値である場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログのエラー 17832 は、状態 9 のエラーを伴います。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-130">When the problem is the **MaxTokenSize** value of the server computer, error 17832 in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log will be accompanied by an error with state 9.</span></span> <span data-ttu-id="3b0f5-131">Kerberos および **MaxTokenSize** の詳細については、[KB327825](https://support.microsoft.com/kb/327825) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-131">For additional details about the Kerberos and **MaxTokenSize**, see [KB327825](https://support.microsoft.com/kb/327825).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3b0f5-132">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="3b0f5-132">User Action</span></span>  
 <span data-ttu-id="3b0f5-133">この問題を解決するには、サーバー コンピューターの **MaxTokenSize** 値を、組織内のユーザーの最も大きなトークンを格納できるサイズに増やします。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-133">To resolve this problem, increase the **MaxTokenSize** value of the server computer, to a size large enough to contain the largest token of any user in your organization.</span></span> <span data-ttu-id="3b0f5-134">組織に適したトークン サイズを調べるには、**Tokensz** アプリケーションの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-134">To research the correct token size for your organization, consider using the **Tokensz** application.</span></span>   
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
 <span data-ttu-id="3b0f5-135">**サーバーコンピューターの MaxTokenSize を変更するには**</span><span class="sxs-lookup"><span data-stu-id="3b0f5-135">**To change the MaxTokenSize  on the server computer**</span></span>  
  
1.  <span data-ttu-id="3b0f5-136">**[スタート]** メニューの **[ファイル名を指定して実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-136">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="3b0f5-137">「」と入力し `regedit` 、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-137">Type `regedit`, and then click **OK**.</span></span> <span data-ttu-id="3b0f5-138">( **[ユーザー アカウント制御]** ダイアログ ボックスが表示されたら、 **[続行]** をクリックします)。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-138">(If the **User Account Control** dialog box appears, click **Continue**.)</span></span>  
  
3.  <span data-ttu-id="3b0f5-139">**HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Lsa\Kerberos\Parameters** に移動します。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-139">Navigate to **HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Lsa\Kerberos\Parameters**.</span></span>  
  
4.  <span data-ttu-id="3b0f5-140">**MaxTokenSize** パラメーターが存在しない場合は、 **[Parameters]** を右クリックし、 **[新規]** をポイントして、 **[DWORD (32 ビット) 値]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-140">If the **MaxTokenSize** parameter is not present, right-click **Parameters**, point to **New**, and then click **DWORD (32-bit)** Value.</span></span> <span data-ttu-id="3b0f5-141">レジストリ エントリに **MaxTokenSize** という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-141">Name the registry entry **MaxTokenSize**.</span></span>  
  
5.  <span data-ttu-id="3b0f5-142">**[MaxTokenSize]** を右クリックし、 **[修正]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-142">Right-click **MaxTokenSize**, and then click **Modify**.</span></span>  
  
6.  <span data-ttu-id="3b0f5-143">**[値のデータ]** ボックスに、目的の **MaxTokenSize** 値を入力します。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-143">In the **Value data** box type the desired **MaxTokenSize** value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3b0f5-144">最大推奨トークン サイズは、16 進数値 ffff (10 進数値 65535) です。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-144">Hexadecimal value ffff (decimal value 65535) is the maximum recommended token size.</span></span> <span data-ttu-id="3b0f5-145">この値を指定することで、ほとんどの場合は問題が解決しますが、コンピューター全体のパフォーマンスに悪影響が出る可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-145">Providing this value would probably solve the problem, but could have negative computer-wide effects with regard to performance.</span></span> <span data-ttu-id="3b0f5-146">組織のユーザーの最も大きなトークンに対応する最小限の **MaxTokenSize** 値を確認し、その値を入力することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-146">We recommend that you establish the minimum **MaxTokenSize** value that allows for the largest token of any user in your organization and enter that value.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="3b0f5-147">**レジストリ エディター**を閉じます。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-147">Close **Registry Editor**.</span></span>  
  
9. <span data-ttu-id="3b0f5-148">コンピューターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="3b0f5-148">Restart the computer.</span></span>  
  
  

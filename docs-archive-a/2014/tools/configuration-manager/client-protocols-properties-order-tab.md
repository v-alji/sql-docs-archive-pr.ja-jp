---
title: クライアントプロトコルのプロパティ ([順序] タブ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- client protocols [SQL Server]
ms.assetid: 64fd7135-1756-4885-bed9-9ab8997ecc6c
author: stevestein
ms.author: sstein
ms.openlocfilehash: a367cff3495389d1a707ed108ba75e1e736538b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713649"
---
# <a name="client-protocols-properties-order-tab"></a><span data-ttu-id="64d0b-102">[クライアント プロトコルのプロパティ] ダイアログ ボックス ([順序] タブ)</span><span class="sxs-lookup"><span data-stu-id="64d0b-102">Client Protocols Properties (Order Tab)</span></span>
  <span data-ttu-id="64d0b-103">**[クライアント プロトコルのプロパティ]** ダイアログ ボックスの **[順序]** ページでは、クライアント プロトコルの表示や有効化を行います。</span><span class="sxs-lookup"><span data-stu-id="64d0b-103">Use the **Order**page on the **Client Protocols Properties** dialog box to view and enable the client protocols.</span></span>  
  
 <span data-ttu-id="64d0b-104">プロトコルをクリックして **[有効化]** または **[無効化]** をクリックすると、選択したプロトコルが **[無効なプロトコル]** 一覧または **[有効なプロトコル]** 一覧に移動します。</span><span class="sxs-lookup"><span data-stu-id="64d0b-104">Click a protocol, and then click **Enable** or **Disable** to move the selected protocol to the **Disabled Protocols** or **Enabled Protocols** list.</span></span>  
  
 <span data-ttu-id="64d0b-105">プロトコルは一覧内の順序で試行されます。つまり、まず最上位のプロトコルで接続が試みられ、次に 2 番目のプロトコルで接続が試みられます。 **[有効なプロトコル]** 一覧のプロトコルを上下に移動するには、上下の矢印ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="64d0b-105">Protocols are tried in the order listed, attempting to connect using the top protocol first, and then the second listed protocol, etc. Move protocols up or down the **Enabled Protocols** list, by clicking the up arrow and down arrow buttons.</span></span> <span data-ttu-id="64d0b-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に同じコンピューター上のクライアントから接続するときに、**共有メモリ** プロトコルが有効になっている場合、常にそのプロトコルが最初に試行されます。</span><span class="sxs-lookup"><span data-stu-id="64d0b-106">When connecting to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a client on that computer, the **Shared Memory** protocol will always be tried first, if enabled.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="64d0b-107">[!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET SqlClient は、これらの設定を使用しません。</span><span class="sxs-lookup"><span data-stu-id="64d0b-107">These settings are not used by [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET SqlClient.</span></span> <span data-ttu-id="64d0b-108">.NET SqlClient のプロトコルの順序は、最初に TCP、次に名前付きパイプであり、この順序は変更できません。</span><span class="sxs-lookup"><span data-stu-id="64d0b-108">The protocol order for .NET SqlClient is first TCP, and then named pipes, which cannot be changed.</span></span>  
  
## <a name="options"></a><span data-ttu-id="64d0b-109">オプション</span><span class="sxs-lookup"><span data-stu-id="64d0b-109">Options</span></span>  
 <span data-ttu-id="64d0b-110">**[無効なプロトコル]**</span><span class="sxs-lookup"><span data-stu-id="64d0b-110">**Disabled Protocols**</span></span>  
 <span data-ttu-id="64d0b-111">インストールされているものの現在使用されていないプロトコルが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="64d0b-111">Lists protocols which are installed but are not currently used.</span></span>  
  
 <span data-ttu-id="64d0b-112">**[有効なプロトコル]**</span><span class="sxs-lookup"><span data-stu-id="64d0b-112">**Enabled Protocols**</span></span>  
 <span data-ttu-id="64d0b-113">このコンピューターのクライアントで使用できるプロトコルの一覧を表示 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="64d0b-113">Lists protocols which are available for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] clients on this computer.</span></span>  
  
 **>**  
 <span data-ttu-id="64d0b-114">**[無効なプロトコル]** ボックス内で現在強調表示されているプロトコルを有効にし、 **[有効なプロトコル]** ボックスに移動します。</span><span class="sxs-lookup"><span data-stu-id="64d0b-114">Enables the currently highlighted protocol in the **Disabled Protocols** box, moving it to the **Enabled Protocols** box.</span></span>  
  
 **\<**  
 <span data-ttu-id="64d0b-115">**[有効なプロトコル]** ボックス内で現在強調表示されているプロトコルを無効にし、 **[無効なプロトコル]** ボックスに移動します。</span><span class="sxs-lookup"><span data-stu-id="64d0b-115">Disables the currently highlighted protocol in the **Enabled Protocols** box, moving it to the **Disabled Protocols** box.</span></span>  
  
 <span data-ttu-id="64d0b-116">上矢印</span><span class="sxs-lookup"><span data-stu-id="64d0b-116">Up arrow</span></span>  
 <span data-ttu-id="64d0b-117">強調表示されているプロトコルを一覧内で上に移動します。</span><span class="sxs-lookup"><span data-stu-id="64d0b-117">Moves the highlighted protocol up in the list.</span></span> <span data-ttu-id="64d0b-118">これにより、Net-Library が接続のためにプロトコルを使用するときの優先順位が上がります。</span><span class="sxs-lookup"><span data-stu-id="64d0b-118">This allows you to increase the priority in which the Net-Library will attempt to use the selected protocol for connections.</span></span>  
  
 <span data-ttu-id="64d0b-119">下矢印</span><span class="sxs-lookup"><span data-stu-id="64d0b-119">Down arrow</span></span>  
 <span data-ttu-id="64d0b-120">強調表示されているプロトコルを一覧内で下に移動します。</span><span class="sxs-lookup"><span data-stu-id="64d0b-120">Moves the highlighted protocol down in the list.</span></span> <span data-ttu-id="64d0b-121">この場合、ネットワーク ライブラリが接続のためにプロトコルを使用するときの優先順位が下がります。</span><span class="sxs-lookup"><span data-stu-id="64d0b-121">This allows you to decrease the priority in which the Net-Library will attempt to use the selected protocol for connections.</span></span>  
  
 <span data-ttu-id="64d0b-122">**[共有メモリ プロトコルを有効にする]**</span><span class="sxs-lookup"><span data-stu-id="64d0b-122">**Enable Shared Memory Protocol**</span></span>  
 <span data-ttu-id="64d0b-123">共有メモリ プロトコルを有効にします。共有メモリ プロトコルが有効になっている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に同じコンピューター上のクライアントから接続するときには常にそのプロトコルが最初に試行されます。</span><span class="sxs-lookup"><span data-stu-id="64d0b-123">Enables the shared memory protocol which is always tried first (if enabled), when connecting to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a client on that computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="64d0b-124">プロトコルをプレフィックスによって指定した場合や、接続文字列の一部として指定した場合は、その指定したプロトコルだけが試行されます。</span><span class="sxs-lookup"><span data-stu-id="64d0b-124">If the protocol is specified through a prefix or as part of the connection string, only the specified protocol is attempted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64d0b-125">参照</span><span class="sxs-lookup"><span data-stu-id="64d0b-125">See Also</span></span>  
 [<span data-ttu-id="64d0b-126">ネットワーク プロトコルの選択</span><span class="sxs-lookup"><span data-stu-id="64d0b-126">Choosing a Network Protocol</span></span>](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  

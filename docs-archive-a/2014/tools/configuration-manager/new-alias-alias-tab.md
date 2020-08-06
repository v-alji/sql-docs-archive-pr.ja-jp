---
title: 新しい別名 ([別名] タブ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 785eb6fb-f67e-449d-b1c8-c38dfbb95ef6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 90742e5de3da0cac83c8b18eebba242ddb9a865d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640298"
---
# <a name="new-alias-alias-tab"></a><span data-ttu-id="059bb-102">[別名 - 新規] ダイアログ ボックス ([別名] タブ)</span><span class="sxs-lookup"><span data-stu-id="059bb-102">New Alias (Alias Tab)</span></span>
  <span data-ttu-id="059bb-103">別名は、接続のために使用できる代替名です。</span><span class="sxs-lookup"><span data-stu-id="059bb-103">An alias is an alternate name that can be used to make a connection.</span></span> <span data-ttu-id="059bb-104">別名は、接続文字列の必須要素をカプセル化したものであり、ユーザーが選択した名前でそれらの要素を公開できます。</span><span class="sxs-lookup"><span data-stu-id="059bb-104">The alias encapsulates the required elements of a connection string, and exposes them with a name chosen by the user.</span></span> <span data-ttu-id="059bb-105">**[別名 - 新規]** ダイアログ ボックスの **[別名]** ページでは、別名の接続文字列の各要素を指定できます。</span><span class="sxs-lookup"><span data-stu-id="059bb-105">Use the **Alias** page on the **Alias - New** dialog box to specify the elements of the connection string for an alias.</span></span> <span data-ttu-id="059bb-106">既存の別名の接続文字列を変更する場合は、「[[&#60;Alias&#62; のプロパティ] ダイアログ ボックス ([別名] タブ)](../../../2014/tools/configuration-manager/alias-properties-alias-tab.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="059bb-106">To change the connection string of an existing alias, see [&#60;Alias&#62; Properties &#40;Alias Tab&#41;](../../../2014/tools/configuration-manager/alias-properties-alias-tab.md).</span></span>  
  
 <span data-ttu-id="059bb-107">**[プロパティ]** グリッドのすべての値を設定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="059bb-107">All values in the **Properties** grid do not have to be completed.</span></span> <span data-ttu-id="059bb-108">有効な組み合わせは、選択したプロトコルによって異なります。</span><span class="sxs-lookup"><span data-stu-id="059bb-108">Valid combinations vary depending on the protocol selected.</span></span> <span data-ttu-id="059bb-109">有効な組み合わせの例については、最後に示してあるトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="059bb-109">See the topics listed below for examples of valid combinations.</span></span>  
  
 <span data-ttu-id="059bb-110">**[別名]**</span><span class="sxs-lookup"><span data-stu-id="059bb-110">**Alias Name**</span></span>  
 <span data-ttu-id="059bb-111">この接続を参照するために使用する名前 (別名) です。</span><span class="sxs-lookup"><span data-stu-id="059bb-111">The name (alias) that you want to use to refer to this connection.</span></span>  
  
 <span data-ttu-id="059bb-112">**[パイプ名]**  /  **[ポート番号]**</span><span class="sxs-lookup"><span data-stu-id="059bb-112">**Pipe Name** / **Port No**</span></span>  
 <span data-ttu-id="059bb-113">接続文字列の追加要素です。</span><span class="sxs-lookup"><span data-stu-id="059bb-113">Additional elements of the connection string.</span></span> <span data-ttu-id="059bb-114">このボックスの名前は、選択したプロトコルによって異なります。</span><span class="sxs-lookup"><span data-stu-id="059bb-114">The name of this box varies with the selected protocol.</span></span>  
  
 <span data-ttu-id="059bb-115">**プロトコル**</span><span class="sxs-lookup"><span data-stu-id="059bb-115">**Protocol**</span></span>  
 <span data-ttu-id="059bb-116">接続に使用するプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="059bb-116">The protocol used for the connection.</span></span>  
  
 <span data-ttu-id="059bb-117">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="059bb-117">**Server**</span></span>  
 <span data-ttu-id="059bb-118">接続先の [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前です。</span><span class="sxs-lookup"><span data-stu-id="059bb-118">The name of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance being connected to.</span></span>  
  
## <a name="when-to-use-an-alias"></a><span data-ttu-id="059bb-119">別名を使用する状況</span><span class="sxs-lookup"><span data-stu-id="059bb-119">When to Use an Alias</span></span>  
 <span data-ttu-id="059bb-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は既定で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル インスタンスに接続するときには **共有メモリ** プロトコルを使用し、別のコンピューター上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続するときには **TCP/IP** または **名前付きパイプ**を使用します。</span><span class="sxs-lookup"><span data-stu-id="059bb-120">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connects to a local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the **Shared Memory** protocol, and to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on another computer using either **TCP/IP** or **Named Pipes**.</span></span> <span data-ttu-id="059bb-121">TCP/IP または名前付きパイプを使用するときにカスタム接続文字列を指定する場合や、接続のためにサーバー名以外の名前を使用する場合には、別名を作成してください。</span><span class="sxs-lookup"><span data-stu-id="059bb-121">Create an alias when you are using TCP/IP or named pipes, and you want to provide a customized connection string, or when you want to use a name other than the server name for the connection.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="059bb-122">例</span><span class="sxs-lookup"><span data-stu-id="059bb-122">Examples</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="059bb-123">が既定の TCP/IP ポート 1433 で受信を待機しない場合に、別のポート番号を設定した接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="059bb-123">is not listening on the default TCP/IP port of 1433 so you want to provide a connection string with a different port number.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="059bb-124">が既定の名前付きパイプで受信を待機しない場合に、別のパイプ名を設定した接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="059bb-124">is not listening on the default named pipe so you want to provide a connection string with a different pipe name.</span></span>  
  
-   <span data-ttu-id="059bb-125">`ACCT`という名前のサーバー上のデータベースに接続するアプリケーションがありますが、そのデータベースは、 `ACCT` という名前のサーバー上の `CENTRAL`という名前のインスタンスとして統合されています。</span><span class="sxs-lookup"><span data-stu-id="059bb-125">An application expects to connect to a database on the server named `ACCT`, but that database has been consolidated as an instance named `ACCT` on a server named `CENTRAL`.</span></span> <span data-ttu-id="059bb-126">そのアプリケーションは、簡単に変更できません。</span><span class="sxs-lookup"><span data-stu-id="059bb-126">The application cannot easily be changed.</span></span> <span data-ttu-id="059bb-127">この場合は、 `ACCT`という別名を作成し、接続文字列で `CENTRAL\ACCT`を参照します。</span><span class="sxs-lookup"><span data-stu-id="059bb-127">Create an alias named `ACCT`, with a connection string pointing to `CENTRAL\ACCT`.</span></span>  
  
## <a name="creating-a-valid-connection-string"></a><span data-ttu-id="059bb-128">有効な接続文字列の作成</span><span class="sxs-lookup"><span data-stu-id="059bb-128">Creating a Valid Connection String</span></span>  
 <span data-ttu-id="059bb-129">別名のプロパティの有効な組み合わせに関する説明と例については、以下のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="059bb-129">See the following topics for a description and examples of valid combinations of alias properties:</span></span>  
  
-   [<span data-ttu-id="059bb-130">共有メモリ プロトコルを使用した有効な接続文字列の作成</span><span class="sxs-lookup"><span data-stu-id="059bb-130">Creating a Valid Connection String Using Shared Memory Protocol</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
-   [<span data-ttu-id="059bb-131">TCP/IP を使用した有効な接続文字列の作成</span><span class="sxs-lookup"><span data-stu-id="059bb-131">Creating a Valid Connection String Using TCP IP</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)  
  
-   [<span data-ttu-id="059bb-132">名前付きパイプを使用した有効な接続文字列の作成</span><span class="sxs-lookup"><span data-stu-id="059bb-132">Creating a Valid Connection String Using Named Pipes</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md)  
  
  

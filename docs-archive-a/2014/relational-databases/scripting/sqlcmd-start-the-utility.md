---
title: sqlcmd ユーティリティの起動
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 00d57437-7a29-4da1-b639-ee990db055fb
author: rothja
ms.author: jroth
ms.openlocfilehash: d71e6f140238599b3f22850ee9b63a0ee25d900b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633035"
---
# <a name="start-the-sqlcmd-utility"></a><span data-ttu-id="ef8d3-102">sqlcmd ユーティリティの起動</span><span class="sxs-lookup"><span data-stu-id="ef8d3-102">Start the sqlcmd Utility</span></span>
  <span data-ttu-id="ef8d3-103">`sqlcmd` を使用するには、最初にユーティリティを起動し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef8d3-103">To begin using `sqlcmd`, you must first launch the utility and connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ef8d3-104">既定のインスタンスまたは名前付きインスタンスのいずれにも接続できます。</span><span class="sxs-lookup"><span data-stu-id="ef8d3-104">You can connect to either a default or named instance.</span></span> <span data-ttu-id="ef8d3-105">最初の手順として、`sqlcmd` ユーティリティを起動します。</span><span class="sxs-lookup"><span data-stu-id="ef8d3-105">The first step is to start the `sqlcmd` utility.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ef8d3-106">`sqlcmd` の既定の認証は Windows 認証です。</span><span class="sxs-lookup"><span data-stu-id="ef8d3-106">Windows Authentication is the default authentication mode for `sqlcmd`.</span></span> <span data-ttu-id="ef8d3-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用するには、 **-U** オプションと **-P** オプションを追加して、ユーザー名とパスワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef8d3-107">To use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, you must specify a user name and password by using the **-U** and **-P** options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ef8d3-108"> 既定では、 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] は名前付きインスタンスの **sqlexpress**としてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="ef8d3-108">By default, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installs as the named instance **sqlexpress**.</span></span>  
  
 <span data-ttu-id="ef8d3-109">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のこのインスタンスに接続したことがない場合、接続を受け入れるには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の構成が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="ef8d3-109">If you have not connected to this instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] before, you may have to configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to accept connections.</span></span>  
  
### <a name="to-start-the-sqlcmd-utility-and-connect-to-a-default-instance-of-sql-server"></a><span data-ttu-id="ef8d3-110">sqlcmd ユーティリティを起動し、SQL Server の既定のインスタンスに接続するには</span><span class="sxs-lookup"><span data-stu-id="ef8d3-110">To start the sqlcmd utility and connect to a default instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="ef8d3-111">[**スタート**] メニューの [**実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ef8d3-111">On the **Start** menu click **Run**.</span></span> <span data-ttu-id="ef8d3-112">**[名前]** ボックスに「 **cmd**」と入力して、 **[OK]** をクリックします。コマンド プロンプト ウィンドウが開きます</span><span class="sxs-lookup"><span data-stu-id="ef8d3-112">In the **Open** box type **cmd**, and then click **OK** to open a Command Prompt window.</span></span>  
  
2.  <span data-ttu-id="ef8d3-113">コマンド プロンプトで、「`sqlcmd`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="ef8d3-113">At the command prompt, type `sqlcmd`.</span></span>  
  
3.  <span data-ttu-id="ef8d3-114">Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="ef8d3-114">Press ENTER.</span></span>  
  
     <span data-ttu-id="ef8d3-115">これで、コンピューターで実行している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のインスタンスに、信頼できる接続を確立しました。</span><span class="sxs-lookup"><span data-stu-id="ef8d3-115">You now have a trusted connection to the default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is running on your computer.</span></span>  
  
     <span data-ttu-id="ef8d3-116">**1>** `sqlcmd` 行番号を指定するプロンプトです。</span><span class="sxs-lookup"><span data-stu-id="ef8d3-116">**1>** is the `sqlcmd` prompt that specifies the line number.</span></span> <span data-ttu-id="ef8d3-117">Enter キーを押すたびに、この番号が 1 ずつ増えます。</span><span class="sxs-lookup"><span data-stu-id="ef8d3-117">Each time you press ENTER, the number increases by one.</span></span>  
  
4.  <span data-ttu-id="ef8d3-118">セッションを終了するには `sqlcmd` 、プロンプトで「」と入力し `EXIT` `sqlcmd` ます。</span><span class="sxs-lookup"><span data-stu-id="ef8d3-118">To end the `sqlcmd` session, type `EXIT` at the `sqlcmd` prompt.</span></span>  
  
### <a name="to-start-the-sqlcmd-utility-and-connect-to-a-named-instance-of-sql-server"></a><span data-ttu-id="ef8d3-119">sqlcmd ユーティリティを起動し、SQL サーバーの名前付きインスタンスに接続するには</span><span class="sxs-lookup"><span data-stu-id="ef8d3-119">To start the sqlcmd utility and connect to a named instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="ef8d3-120">コマンドプロンプトウィンドウを開き、「 `sqlcmd -S` *My\ インスタンス*名」と入力します。</span><span class="sxs-lookup"><span data-stu-id="ef8d3-120">Open a Command Prompt window, and type `sqlcmd -S`*myServer\instanceName*.</span></span> <span data-ttu-id="ef8d3-121">*myServer\instanceName* には、コンピューターの実際の名前と、接続先の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを指定してください。</span><span class="sxs-lookup"><span data-stu-id="ef8d3-121">Replace *myServer\instanceName* with the name of the computer and the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to connect to.</span></span>  
  
2.  <span data-ttu-id="ef8d3-122">Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="ef8d3-122">Press ENTER.</span></span>  
  
     <span data-ttu-id="ef8d3-123">`sqlcmd`プロンプト (1>) は、指定したのインスタンスに接続していることを示し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="ef8d3-123">The `sqlcmd` prompt (1>) indicates that you are connected to the specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ef8d3-124">入力した [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントはバッファーに格納されます。</span><span class="sxs-lookup"><span data-stu-id="ef8d3-124">Entered [!INCLUDE[tsql](../../includes/tsql-md.md)] statements are stored in a buffer.</span></span> <span data-ttu-id="ef8d3-125">GO コマンドが見つかると、ステートメントがバッチとして実行されます。</span><span class="sxs-lookup"><span data-stu-id="ef8d3-125">They are executed as a batch when the GO command is encountered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef8d3-126">参照</span><span class="sxs-lookup"><span data-stu-id="ef8d3-126">See Also</span></span>  
 [<span data-ttu-id="ef8d3-127">sqlcmd を使用した Transact-SQL スクリプト ファイルの実行</span><span class="sxs-lookup"><span data-stu-id="ef8d3-127">Run Transact-SQL Script Files Using sqlcmd</span></span>](sqlcmd-run-transact-sql-script-files.md)  
  
  

---
title: プログラムの例外メッセージボックス |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- exception message box [SQL Server]
- displaying exception message box
ms.assetid: c771985b-149c-459a-b3cb-7b15fde01150
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9d49bdf8c73f86b2c334018d40510b4ae67c85ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741230"
---
# <a name="program-exception-message-box"></a><span data-ttu-id="251ff-102">例外メッセージ ボックスのプログラミング</span><span class="sxs-lookup"><span data-stu-id="251ff-102">Program Exception Message Box</span></span>
  <span data-ttu-id="251ff-103">例外メッセージ ボックスをアプリケーションで使用すると、<xref:System.Windows.Forms.MessageBox> クラスを使用した場合よりも高い柔軟性で、メッセージ エクスペリエンスを制御することができます。</span><span class="sxs-lookup"><span data-stu-id="251ff-103">You can use the exception message box in your applications to provide significantly more control over the messaging experience than is provided by the <xref:System.Windows.Forms.MessageBox> class.</span></span> <span data-ttu-id="251ff-104">詳細については、「[例外メッセージボックスのプログラミング](../../../2014/database-engine/dev-guide/exception-message-box-programming.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="251ff-104">For more information, see [Exception Message Box Programming](../../../2014/database-engine/dev-guide/exception-message-box-programming.md).</span></span> <span data-ttu-id="251ff-105">例外メッセージ ボックス .dll を取得および展開する方法の詳細については、「 [Deploying an Exception Message Box Application](../../../2014/database-engine/dev-guide/deploying-an-exception-message-box-application.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="251ff-105">For information about how to obtain and deploy the exception message box .dll, see [Deploying an Exception Message Box Application](../../../2014/database-engine/dev-guide/deploying-an-exception-message-box-application.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="251ff-106">手順</span><span class="sxs-lookup"><span data-stu-id="251ff-106">Procedure</span></span>  
  
#### <a name="to-handle-an-exception-by-using-the-exception-message-box"></a><span data-ttu-id="251ff-107">例外メッセージ ボックスを使用して例外を処理するには</span><span class="sxs-lookup"><span data-stu-id="251ff-107">To handle an exception by using the exception message box</span></span>  
  
1.  <span data-ttu-id="251ff-108">Microsoft.ExceptionMessageBox.dll アセンブリへの参照をマネージド コード プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="251ff-108">Add a reference in your managed code project to the Microsoft.ExceptionMessageBox.dll assembly.</span></span>  
  
2.  <span data-ttu-id="251ff-109">Optional`using`(C#) または `Imports` ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .net) ディレクティブを追加して、名前空間を使用し <xref:Microsoft.SqlServer.MessageBox> ます。</span><span class="sxs-lookup"><span data-stu-id="251ff-109">(Optional) Add a `using` (C#) or `Imports` ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET) directive to use the <xref:Microsoft.SqlServer.MessageBox> namespace.</span></span>  
  
3.  <span data-ttu-id="251ff-110">予想される例外を処理する try-catch ブロックを作成します。</span><span class="sxs-lookup"><span data-stu-id="251ff-110">Create a try-catch block to handle the anticipated exception.</span></span>  
  
4.  <span data-ttu-id="251ff-111">`catch` ブロック内に、<xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="251ff-111">Within the `catch` block, create an instance of the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> class.</span></span> <span data-ttu-id="251ff-112"><xref:System.Exception>ブロックによって処理されるオブジェクトを渡し `try` - `catch` ます。</span><span class="sxs-lookup"><span data-stu-id="251ff-112">Pass the <xref:System.Exception> object handled by the `try`-`catch` block.</span></span>  
  
5.  <span data-ttu-id="251ff-113">(省略可) <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> に次のプロパティを 1 つ以上設定します。</span><span class="sxs-lookup"><span data-stu-id="251ff-113">(Optional) Set one or more of the following properties on <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox>:</span></span>  
  
    -   <span data-ttu-id="251ff-114"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons>例外メッセージボックスに表示するボタンを指定する列挙です。</span><span class="sxs-lookup"><span data-stu-id="251ff-114"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons> enumeration that specifies the buttons to display in the exception message box.</span></span>  
  
    -   <span data-ttu-id="251ff-115"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.DefaultButton%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDefaultButton>例外メッセージボックスの既定のボタンを指定する列挙です。</span><span class="sxs-lookup"><span data-stu-id="251ff-115"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.DefaultButton%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDefaultButton> enumeration that specifies the default button for the exception message box.</span></span>  
  
    -   <span data-ttu-id="251ff-116"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Options%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxOptions>例外メッセージボックスのその他の動作を制御するために使用する列挙です。</span><span class="sxs-lookup"><span data-stu-id="251ff-116"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Options%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxOptions> enumeration that you use to control other behaviors of the exception message box.</span></span>  
  
    -   <span data-ttu-id="251ff-117"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Symbol%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxSymbol>例外メッセージボックスに表示する記号を指定する列挙です。</span><span class="sxs-lookup"><span data-stu-id="251ff-117"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Symbol%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxSymbol> enumeration that specifies the symbol to display in the exception message box.</span></span>  
  
6.  <span data-ttu-id="251ff-118"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="251ff-118">Call the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> method.</span></span> <span data-ttu-id="251ff-119">例外メッセージ ボックスが属する親ウィンドウを渡します。</span><span class="sxs-lookup"><span data-stu-id="251ff-119">Pass the parent window to which the exception message box belongs.</span></span>  
  
7.  <span data-ttu-id="251ff-120">Optional<xref:System.Windows.Forms.DialogResult>ユーザーがクリックしたボタンを判断する必要がある場合は、返された列挙体の値を確認します。</span><span class="sxs-lookup"><span data-stu-id="251ff-120">(Optional) Note the value of returned <xref:System.Windows.Forms.DialogResult> enumeration if you need to determine which button the user clicked.</span></span>  
  
#### <a name="to-display-the-exception-message-box-without-an-exception"></a><span data-ttu-id="251ff-121">例外なしで例外メッセージ ボックスを表示するには</span><span class="sxs-lookup"><span data-stu-id="251ff-121">To display the exception message box without an exception</span></span>  
  
1.  <span data-ttu-id="251ff-122">Microsoft.ExceptionMessageBox.dll アセンブリへの参照をマネージド コード プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="251ff-122">Add a reference in your managed code project to the Microsoft.ExceptionMessageBox.dll assembly.</span></span>  
  
2.  <span data-ttu-id="251ff-123">Optional`using`(C#) または `Imports` (Visual Basic .net) ディレクティブを追加して、名前空間を使用し <xref:Microsoft.SqlServer.MessageBox> ます。</span><span class="sxs-lookup"><span data-stu-id="251ff-123">(Optional) Add a `using` (C#) or `Imports` (Visual Basic .NET) directive to use the <xref:Microsoft.SqlServer.MessageBox> namespace.</span></span>  
  
3.  <span data-ttu-id="251ff-124"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="251ff-124">Create an instance of the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> class.</span></span> <span data-ttu-id="251ff-125"><xref:System.String> 値としてメッセージ テキストを渡します。</span><span class="sxs-lookup"><span data-stu-id="251ff-125">Pass the message text as a <xref:System.String> value.</span></span>  
  
4.  <span data-ttu-id="251ff-126">(省略可) <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> に次のプロパティを 1 つ以上設定します。</span><span class="sxs-lookup"><span data-stu-id="251ff-126">(Optional) Set one or more of the following properties on <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox>:</span></span>  
  
    -   <span data-ttu-id="251ff-127"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons>例外メッセージボックスに表示するボタンを指定する列挙です。</span><span class="sxs-lookup"><span data-stu-id="251ff-127"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons> enumeration that specifies the buttons to display in the exception message box.</span></span>  
  
    -   <span data-ttu-id="251ff-128"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Caption%2A> - 例外メッセージ ボックスのダイアログ ボックスのキャプションです。</span><span class="sxs-lookup"><span data-stu-id="251ff-128"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Caption%2A> - Dialog box caption of the exception message box.</span></span>  
  
    -   <span data-ttu-id="251ff-129"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.DefaultButton%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDefaultButton>例外メッセージボックスのダイアログボックスの既定のボタンを指定する列挙です。</span><span class="sxs-lookup"><span data-stu-id="251ff-129"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.DefaultButton%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDefaultButton> enumeration that specifies the default button for the dialog box of the exception message box.</span></span>  
  
    -   <span data-ttu-id="251ff-130"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Options%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxOptions>例外メッセージボックスのその他の動作を制御するために使用する列挙です。</span><span class="sxs-lookup"><span data-stu-id="251ff-130"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Options%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxOptions> enumeration that you use to control other behaviors of the exception message box.</span></span>  
  
    -   <span data-ttu-id="251ff-131"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Symbol%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxSymbol>例外メッセージボックスに表示する記号を指定する列挙です。</span><span class="sxs-lookup"><span data-stu-id="251ff-131"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Symbol%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxSymbol> enumeration that specifies the symbol to display in the exception message box.</span></span>  
  
5.  <span data-ttu-id="251ff-132"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="251ff-132">Call the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> method.</span></span> <span data-ttu-id="251ff-133">例外メッセージ ボックスが属する親ウィンドウを渡します。</span><span class="sxs-lookup"><span data-stu-id="251ff-133">Pass the parent window to which the exception message box belongs.</span></span>  
  
6.  <span data-ttu-id="251ff-134">(省略可) ユーザーがクリックしたボタンを判断する必要がある場合は、返された <xref:System.Windows.Forms.DialogResult> 列挙値に注意します。</span><span class="sxs-lookup"><span data-stu-id="251ff-134">(Optional) Note the value of the returned <xref:System.Windows.Forms.DialogResult> enumeration if you need to determine which button the user clicked.</span></span>  
  
#### <a name="to-display-the-exception-message-box-with-customized-buttons"></a><span data-ttu-id="251ff-135">カスタマイズされたボタンのある例外メッセージ ボックスを表示するには</span><span class="sxs-lookup"><span data-stu-id="251ff-135">To display the exception message box with customized buttons</span></span>  
  
1.  <span data-ttu-id="251ff-136">Microsoft.ExceptionMessageBox.dll アセンブリへの参照をマネージド コード プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="251ff-136">Add a reference in your managed code project to the Microsoft.ExceptionMessageBox.dll assembly.</span></span>  
  
2.  <span data-ttu-id="251ff-137">Optional`using`(C#) または `Imports` (Visual Basic .net) ディレクティブを追加して、名前空間を使用し <xref:Microsoft.SqlServer.MessageBox> ます。</span><span class="sxs-lookup"><span data-stu-id="251ff-137">(Optional) Add a `using` (C#) or `Imports` (Visual Basic .NET) directive to use the <xref:Microsoft.SqlServer.MessageBox> namespace.</span></span>  
  
3.  <span data-ttu-id="251ff-138">次の 2 つのうち、いずれかの方法で <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="251ff-138">Create an instance of the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> class in one of two ways:</span></span>  
  
    -   <span data-ttu-id="251ff-139"><xref:System.Exception>ブロックによって処理されるオブジェクトを渡し `try` - `catch` ます。</span><span class="sxs-lookup"><span data-stu-id="251ff-139">Pass the <xref:System.Exception> object handled by a `try`-`catch` block.</span></span>  
  
    -   <span data-ttu-id="251ff-140"><xref:System.String> 値としてメッセージ テキストを渡します。</span><span class="sxs-lookup"><span data-stu-id="251ff-140">Pass the message text as a <xref:System.String> value.</span></span>  
  
4.  <span data-ttu-id="251ff-141"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> に次のいずれかの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="251ff-141">Set one of the following values for <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A>:</span></span>  
  
    -   <span data-ttu-id="251ff-142"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.AbortRetryIgnore>-[**中止**]、[**再試行**]、および [**無視**] ボタンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="251ff-142"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.AbortRetryIgnore> - displays the **Abort**, **Retry**, and **Ignore** buttons.</span></span>  
  
    -   <span data-ttu-id="251ff-143"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.Custom> - カスタム ボタンを表示します。</span><span class="sxs-lookup"><span data-stu-id="251ff-143"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.Custom> - displays custom buttons.</span></span>  
  
    -   <span data-ttu-id="251ff-144"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.OK>- **[OK** ] ボタンを表示します。</span><span class="sxs-lookup"><span data-stu-id="251ff-144"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.OK> - displays the **OK** button.</span></span>  
  
    -   <span data-ttu-id="251ff-145"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.OKCancel>- **[OK]** ボタンと **[キャンセル**] ボタンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="251ff-145"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.OKCancel> - displays the **OK** and **Cancel** buttons.</span></span>  
  
    -   <span data-ttu-id="251ff-146"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.RetryCancel>-[**再試行**] ボタンと **[キャンセル]** ボタンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="251ff-146"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.RetryCancel> - displays the **Retry** and **Cancel** buttons.</span></span>  
  
    -   <span data-ttu-id="251ff-147"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.YesNo>- **[はい] および [** **いいえ**] ボタンを表示します。</span><span class="sxs-lookup"><span data-stu-id="251ff-147"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.YesNo> - displays **Yes** and **No** buttons.</span></span>  
  
    -   <span data-ttu-id="251ff-148"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.YesNoCancel>- **[はい**]、[**いいえ**]、および **[キャンセル**] の各ボタンを表示します。</span><span class="sxs-lookup"><span data-stu-id="251ff-148"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.YesNoCancel> - displays **Yes**, **No**, and **Cancel** buttons.</span></span>  
  
5.  <span data-ttu-id="251ff-149">(省略可) カスタム ボタンを使用する場合は、<xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.SetButtonText%2A> メソッドのオーバーロードの 1 つを呼び出し、最多で 5 つのカスタム ボタンのテキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="251ff-149">(Optional) If you use custom buttons, call one of the overloads of the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.SetButtonText%2A> method to specify text for up to five custom buttons.</span></span>  
  
6.  <span data-ttu-id="251ff-150"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="251ff-150">Call the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> method.</span></span> <span data-ttu-id="251ff-151">例外メッセージ ボックスが属する親ウィンドウを渡します。</span><span class="sxs-lookup"><span data-stu-id="251ff-151">Pass the parent window to which the exception message box belongs.</span></span>  
  
7.  <span data-ttu-id="251ff-152">(省略可) ユーザーがクリックしたボタンを判断する必要がある場合は、返された <xref:System.Windows.Forms.DialogResult> 列挙値に注意します。</span><span class="sxs-lookup"><span data-stu-id="251ff-152">(Optional) Note the value of the returned <xref:System.Windows.Forms.DialogResult> enumeration if you need to determine which button the user clicked.</span></span> <span data-ttu-id="251ff-153">カスタム ボタンを使用する場合に、ユーザーがクリックしたボタンを判断するには、<xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDialogResult> プロパティの <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CustomDialogResult%2A> の値に注意します。</span><span class="sxs-lookup"><span data-stu-id="251ff-153">If you use custom buttons, note the value of <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDialogResult> for the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CustomDialogResult%2A> property to determine which of the custom buttons the user clicked.</span></span>  
  
#### <a name="to-allow-users-to-decide-whether-to-show-the-exception-message-box"></a><span data-ttu-id="251ff-154">ユーザーが例外メッセージ ボックスを表示するかどうかを決定できるようにするには</span><span class="sxs-lookup"><span data-stu-id="251ff-154">To allow users to decide whether to show the exception message box</span></span>  
  
1.  <span data-ttu-id="251ff-155">Microsoft.ExceptionMessageBox.dll アセンブリへの参照をマネージド コード プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="251ff-155">Add a reference in your managed code project to the Microsoft.ExceptionMessageBox.dll assembly.</span></span>  
  
2.  <span data-ttu-id="251ff-156">Optional`using`(C#) または `Imports` (Visual Basic .net) ディレクティブを追加して、名前空間を使用し <xref:Microsoft.SqlServer.MessageBox> ます。</span><span class="sxs-lookup"><span data-stu-id="251ff-156">(Optional) Add a `using` (C#) or `Imports` (Visual Basic .NET) directive to use the <xref:Microsoft.SqlServer.MessageBox> namespace.</span></span>  
  
3.  <span data-ttu-id="251ff-157">次の 2 つのうち、いずれかの方法で <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="251ff-157">Create an instance of the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> class in one of two ways:</span></span>  
  
    -   <span data-ttu-id="251ff-158"><xref:System.Exception>ブロックによって処理されるオブジェクトを渡し `try` - `catch` ます。</span><span class="sxs-lookup"><span data-stu-id="251ff-158">Pass the <xref:System.Exception> object handled by a `try`-`catch` block.</span></span>  
  
    -   <span data-ttu-id="251ff-159"><xref:System.String> 値としてメッセージ テキストを渡します。</span><span class="sxs-lookup"><span data-stu-id="251ff-159">Pass the message text as a <xref:System.String> value.</span></span>  
  
4.  <span data-ttu-id="251ff-160"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.ShowCheckbox%2A> プロパティを `true`に設定します。</span><span class="sxs-lookup"><span data-stu-id="251ff-160">Set the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.ShowCheckbox%2A> property to `true`.</span></span>  
  
5.  <span data-ttu-id="251ff-161">(省略可) 表示された例外メッセージ ボックスを再度表示するかどうかを確認するテキストを <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxText%2A> に指定します。</span><span class="sxs-lookup"><span data-stu-id="251ff-161">(Optional) Specify the text that asks the user to decide whether to show the exception message box again for <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxText%2A>.</span></span> <span data-ttu-id="251ff-162">既定のテキストは、"今後、このメッセージを表示しない" です。</span><span class="sxs-lookup"><span data-stu-id="251ff-162">The default text is "Do not show this message again."</span></span>  
  
6.  <span data-ttu-id="251ff-163">アプリケーションが実行されている間のみユーザーの指定を保持する場合は、<xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.IsCheckboxChecked%2A> の値をグローバルな <xref:System.Boolean> 変数に設定します。</span><span class="sxs-lookup"><span data-stu-id="251ff-163">If you need to keep the user's decision only for the duration of the application's execution, set the value of <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.IsCheckboxChecked%2A> to a global <xref:System.Boolean> variable.</span></span> <span data-ttu-id="251ff-164">例外メッセージ ボックスのインスタンスを作成する前に、この値を評価します。</span><span class="sxs-lookup"><span data-stu-id="251ff-164">Evaluate this value before creating an instance of the exception message box.</span></span>  
  
7.  <span data-ttu-id="251ff-165">ユーザーの指定を永続的に保持する必要がある場合は、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="251ff-165">If you need to store a user's decision permanently, do the following:</span></span>  
  
    1.  <span data-ttu-id="251ff-166">CreateSubKe メソッドを呼び出して、アプリケーションが使用するカスタム レジストリ キーを開き、<xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryKey%2A> に返された RegistryKey オブジェクトを設定します。</span><span class="sxs-lookup"><span data-stu-id="251ff-166">Call the CreateSubKey method to open a custom registry key that your application uses, and set <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryKey%2A> to the returned RegistryKey object.</span></span>  
  
    2.  <span data-ttu-id="251ff-167"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryValue%2A> に使用するレジストリの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="251ff-167">Set <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryValue%2A> to the name of the registry value that is used.</span></span>  
  
    3.  <span data-ttu-id="251ff-168"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryMeansDoNotShowDialog%2A> を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="251ff-168">Set <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryMeansDoNotShowDialog%2A> to `true`.</span></span>  
  
    4.  <span data-ttu-id="251ff-169"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="251ff-169">Call the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> method.</span></span> <span data-ttu-id="251ff-170">指定したレジストリ キーが評価され、レジストリ キーに格納されているデータが 0 の場合にのみ、例外メッセージ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="251ff-170">The specified registry key is evaluated, and the exception message box is displayed only if the data stored in the registry key is 0.</span></span> <span data-ttu-id="251ff-171">ダイアログ ボックスが表示され、ユーザーがボタンをクリックする前にチェック ボックスをオンにした場合は、レジストリ キーのデータが 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="251ff-171">If the dialog box is displayed and the user selects the check box before clicking a button, the data in the registry key is set to 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="251ff-172">例</span><span class="sxs-lookup"><span data-stu-id="251ff-172">Example</span></span>  
 <span data-ttu-id="251ff-173">この例では、例外メッセージボックスを **[OK** ] ボタンのみと共に使用して、処理された例外とアプリケーション固有の追加情報を含むアプリケーション例外の情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="251ff-173">This example uses the exception message box with only the **OK** button to display information from an application exception that includes the handled exception along with additional application-specific information.</span></span>  
  
 [!code-csharp[HowTo#emb_showOKbutton](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_showokbutton)]  
  
 [!code-vb[HowTo#emb_vb_showOKbutton](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_showokbutton)]  
  
## <a name="example"></a><span data-ttu-id="251ff-174">例</span><span class="sxs-lookup"><span data-stu-id="251ff-174">Example</span></span>  
 <span data-ttu-id="251ff-175">この例では、ユーザーが選択した **[はい] と [** **いいえ**] ボタンを使用して、例外メッセージボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="251ff-175">This example uses the exception message box with **Yes** and **No** buttons from which the user chooses.</span></span>  
  
 [!code-csharp[HowTo#emb_showYesNobutton](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_showyesnobutton)]  
  
 [!code-vb[HowTo#emb_vb_showYesNobutton](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_showyesnobutton)]  
  
## <a name="example"></a><span data-ttu-id="251ff-176">例</span><span class="sxs-lookup"><span data-stu-id="251ff-176">Example</span></span>  
 <span data-ttu-id="251ff-177">次の例では、カスタム ボタンのある例外メッセージ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="251ff-177">This example uses the exception message box with custom buttons.</span></span>  
  
 [!code-csharp[HowTo#emb_showcustombutton](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_showcustombutton)]  
  
 [!code-vb[HowTo#emb_vb_showcustombutton](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_showcustombutton)]  
  
## <a name="example"></a><span data-ttu-id="251ff-178">例</span><span class="sxs-lookup"><span data-stu-id="251ff-178">Example</span></span>  
 <span data-ttu-id="251ff-179">次の例では、チェック ボックスを使用して、例外メッセージ ボックスを表示するかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="251ff-179">This example uses the check box to determine whether to show the exception message box.</span></span>  
  
 [!code-csharp[HowTo#emb_usecheckbox](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_usecheckbox)]  
  
 [!code-vb[HowTo#emb_vb_usecheckbox](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_usecheckbox)]  
  
## <a name="example"></a><span data-ttu-id="251ff-180">例</span><span class="sxs-lookup"><span data-stu-id="251ff-180">Example</span></span>  
 <span data-ttu-id="251ff-181">次の例では、チェック ボックスとレジストリ キーを使用して、例外メッセージ ボックスを表示するかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="251ff-181">This example uses the check box and a registry key to determine whether to show the exception message box.</span></span>  
  
 [!code-csharp[HowTo#emb_useregkey](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_useregkey)]  
  
 [!code-vb[HowTo#emb_vb_useregkey](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_useregkey)]  
  
## <a name="example"></a><span data-ttu-id="251ff-182">例</span><span class="sxs-lookup"><span data-stu-id="251ff-182">Example</span></span>  
 <span data-ttu-id="251ff-183">この例では、例外メッセージ ボックスを使用して、トラブルシューティングやデバッグに役立つ追加情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="251ff-183">This example uses the exception message box to show additional information that is helpful when troubleshooting or debugging.</span></span>  
  
 [!code-csharp[HowTo#emb_moreinfo](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_moreinfo)]  
  
 [!code-vb[HowTo#emb_vb_moreinfo](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_moreinfo)]  
  
  

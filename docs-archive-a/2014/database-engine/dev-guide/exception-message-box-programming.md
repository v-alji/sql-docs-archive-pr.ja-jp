---
title: 例外メッセージボックスのプログラミング |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- ExceptionMessageBox class, about ExceptionMessageBox class
- exception message box [SQL Server], about exception message box
- exception message box [SQL Server]
- interfaces [SQL Server]
- exceptions [SQL Server]
- messages [SQL Server], exception message box
ms.assetid: 0b1ba514-6959-4e69-bfd2-3cf3c1ac4b9c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b2425169f838199ce24b4331dd57c74b480adf62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742537"
---
# <a name="exception-message-box-programming"></a><span data-ttu-id="fc5d8-102">例外メッセージ ボックスのプログラミング</span><span class="sxs-lookup"><span data-stu-id="fc5d8-102">Exception Message Box Programming</span></span>
  <span data-ttu-id="fc5d8-103">例外メッセージボックスは、グラフィカルコンポーネントと共にインストールされ、使用されるプログラムインターフェイスです [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-103">The exception message box is a programmatic interface that is installed with and used by [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] graphical components.</span></span> <span data-ttu-id="fc5d8-104">例外メッセージ ボックスは、サポートされるマネージド アセンブリです。アプリケーションで例外メッセージ ボックスを使用することで、メッセージ エクスペリエンスを高い柔軟性で制御し、ユーザーが後で参照できるようにエラー メッセージを保存したり、メッセージのヘルプを表示できるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-104">The exception message box is a supported managed assembly that you can use in your applications to provide significantly more control over the messaging experience and to give your users the options to save error message content for later reference and to get help on messages.</span></span> <span data-ttu-id="fc5d8-105">例外メッセージボックスは、を除くのすべてのエディションでインストールされるため [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)] 、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントコンポーネントがインストールされているコンピューターでは、追加の構成なしで使用できます。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-105">Because the exception message box is installed by all editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] except [!INCLUDE[ssEW](../../includes/ssew-md.md)], you can use it with no additional configuration on any computer on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client components have been installed.</span></span>  
  
 <span data-ttu-id="fc5d8-106"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> 名前空間の <xref:Microsoft.SqlServer.MessageBox> クラスには、<xref:System.Windows.Forms.MessageBox> クラスなどの全機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-106">The <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> class in the <xref:Microsoft.SqlServer.MessageBox> namespace has all the functionality of the <xref:System.Windows.Forms.MessageBox> class and more.</span></span> <span data-ttu-id="fc5d8-107"><xref:System.Windows.Forms.MessageBox> はマネージド コード例外を効率よく処理できるように設計されており、<xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> の使用が考えられる作業に最適です。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-107">Ideal for any tasks for which <xref:System.Windows.Forms.MessageBox> may be used, <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> is designed to elegantly handle managed code exceptions.</span></span> <span data-ttu-id="fc5d8-108">例外メッセージ ボックスを使用することで、次のことが可能になります。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-108">The exception message box allows you to do the following:</span></span>  
  
-   <span data-ttu-id="fc5d8-109">カスタマイズされたボタン テキストを最大 5 個まで提供できます。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-109">Provide customized button text for up to five buttons.</span></span> <span data-ttu-id="fc5d8-110">ボタンやダイアログ ボックスのサイズは、各テキストの長さに応じて自動的に変更されます。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-110">Buttons and the dialog box resize automatically for different text lengths.</span></span>  
  
-   <span data-ttu-id="fc5d8-111">メッセージのタイトル、テキスト、ボタン テキスト、ヘルプ リンクがある場合は、ユーザーがこれらをクリップボードにコピーしたり、この情報を電子メール メッセージで送信できます。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-111">Allow users to easily copy the message title, text, button text, and help links (if any) to the Clipboard or send this information in an e-mail message.</span></span>  
  
-   <span data-ttu-id="fc5d8-112">ユーザーが**追加情報**をクリックしたときに、すべての基になる例外とエラーを階層リレーションシップツリーに表示します。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-112">Display all underlying exceptions and errors in a hierarchical relationship tree when users click **Additional Information**.</span></span>  
  
-   <span data-ttu-id="fc5d8-113">同じ例外が再度発生した場合に、メッセージを表示するかどうかをユーザーが決定できます。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-113">Allow users to decide whether to display the message when the same exception occurs again.</span></span>  
  
-   <span data-ttu-id="fc5d8-114">例外に関連付けられたヘルプ リンクを使って、オンライン ヘルプ システムにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-114">Access an online help system by using a help link associated with the exception.</span></span>  
  
 <span data-ttu-id="fc5d8-115">詳細については、「[プログラム例外メッセージボックス](../../../2014/database-engine/dev-guide/program-exception-message-box.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-115">For more information, see [Program Exception Message Box](../../../2014/database-engine/dev-guide/program-exception-message-box.md).</span></span>  
  
  

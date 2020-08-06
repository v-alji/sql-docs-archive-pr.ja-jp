---
title: カスタム ログ プロバイダー用ユーザー インターフェイスの開発 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom user interface [Integration Services], custom log providers
- custom log providers [Integration Services], developing custom user interface
ms.assetid: 6fd2d269-d87a-4134-82a1-40a09b3b5453
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c3ce6cf5ad744e307bbb049347047bf94fc5a908
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632624"
---
# <a name="developing-a-user-interface-for-a-custom-log-provider"></a><span data-ttu-id="88bbf-102">カスタム ログ プロバイダー用ユーザー インターフェイスの開発</span><span class="sxs-lookup"><span data-stu-id="88bbf-102">Developing a User Interface for a Custom Log Provider</span></span>
  <span data-ttu-id="88bbf-103">多くの [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ログ プロバイダーには、カスタム ユーザー インターフェイスがあります。カスタム ユーザー インターフェイスには <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI> が実装され、**[SSIS ログの構成]** ダイアログ ボックスの **[構成]** ボックスが、使用可能な接続マネージャーがフィルター選択されたドロップダウン リストに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="88bbf-103">Many [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] log providers have a custom user interface that implements <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI> and replaces the **Configuration** text box in the **Configure SSIS Logs** dialog box with a filtered dropdown list of available connection managers.</span></span> <span data-ttu-id="88bbf-104">ただし、カスタム ログ プロバイダーのカスタム ユーザー インターフェイスは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] では実装されていません。</span><span class="sxs-lookup"><span data-stu-id="88bbf-104">However, custom user interfaces for custom log providers are not implemented in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>  
  
<span data-ttu-id="88bbf-105">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="88bbf-105">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="88bbf-106">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="88bbf-106">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="88bbf-107">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="88bbf-107">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="88bbf-108">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="88bbf-108">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88bbf-109">参照</span><span class="sxs-lookup"><span data-stu-id="88bbf-109">See Also</span></span>  
 <span data-ttu-id="88bbf-110">[カスタム ログ プロバイダーの作成](creating-a-custom-log-provider.md) </span><span class="sxs-lookup"><span data-stu-id="88bbf-110">[Creating a Custom Log Provider](creating-a-custom-log-provider.md) </span></span>  
 [<span data-ttu-id="88bbf-111">カスタム ログ プロバイダーのコーディング</span><span class="sxs-lookup"><span data-stu-id="88bbf-111">Coding a Custom Log Provider</span></span>](coding-a-custom-log-provider.md)  
  
  

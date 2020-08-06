---
title: スクリプティング ソリューションとカスタム オブジェクトとの比較 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- managed tasks [Integration Services]
- Script task [Integration Services], vs. custom managed tasks
- SSIS Script task, vs. custom managed tasks
- custom tasks [Integration Services], scripts
ms.assetid: c0aea822-a21e-44e1-a3d3-8777bd0a1c34
author: chugugrace
ms.author: chugu
ms.openlocfilehash: acf6faf9cdd78e951b8298c4e3b144d3444fb1ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632617"
---
# <a name="comparing-scripting-solutions-and-custom-objects"></a><span data-ttu-id="de373-102">スクリプティング ソリューションとカスタム オブジェクトとの比較</span><span class="sxs-lookup"><span data-stu-id="de373-102">Comparing Scripting Solutions and Custom Objects</span></span>
  <span data-ttu-id="de373-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] スクリプト タスクまたはスクリプト コンポーネントは、カスタム マネージド タスクまたはデータ フロー コンポーネントで使用できる機能とほぼ同じ機能を実装できます。</span><span class="sxs-lookup"><span data-stu-id="de373-103">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Script task or Script component can implement much of the same functionality that is possible in a custom managed task or data flow component.</span></span> <span data-ttu-id="de373-104">ここでは、適切な種類のタスクを必要に応じて選択するときに役立つ注意事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="de373-104">Here are some considerations to help you choose the appropriate type of task for your needs:</span></span>  
  
-   <span data-ttu-id="de373-105">構成または機能が個々のパッケージに固有である場合は、カスタム オブジェクトを開発する代わりに、スクリプト タスクまたはスクリプト コンポーネントを使用します。</span><span class="sxs-lookup"><span data-stu-id="de373-105">If the configuration or functionality is specific to an individual package, you should use the Script task or the Script component instead of a developing a custom object.</span></span>  
  
-   <span data-ttu-id="de373-106">機能が汎用で、将来は他のパッケージ用に使用されたり、他の開発者が使用する可能性がある場合は、スクリプト ソリューションを使用する代わりに、カスタム オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="de373-106">If the functionality is generic, and might be used in the future for other packages and by other developers, you should create a custom object instead of using a scripting solution.</span></span> <span data-ttu-id="de373-107">カスタム オブジェクトは任意のパッケージで使用できますが、スクリプトは、そのスクリプトが作成されたパッケージでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="de373-107">You can use a custom object in any package, whereas a script can be used only in the package for which it was created.</span></span>  
  
-   <span data-ttu-id="de373-108">同じパッケージ内でコードを再使用する場合、カスタム オブジェクトを作成することを検討します。</span><span class="sxs-lookup"><span data-stu-id="de373-108">If the code will be reused within the same package, you should consider creating a custom object.</span></span> <span data-ttu-id="de373-109">あるスクリプト タスクまたはコンポーネントから別のスクリプト タスクまたはコンポーネントにコードをコピーすると、コードの複数コピーの維持および更新が煩雑になるため、管理が難しくなります。</span><span class="sxs-lookup"><span data-stu-id="de373-109">Copying code from one Script task or component to another leads to reduced maintainability by making it more difficult to maintain and update multiple copies of the code.</span></span>  
  
-   <span data-ttu-id="de373-110">将来的に実装方法を変更する場合は、カスタム オブジェクトの使用を検討します。</span><span class="sxs-lookup"><span data-stu-id="de373-110">If the implementation will change over time, consider using a custom object.</span></span> <span data-ttu-id="de373-111">カスタム オブジェクトは、親パッケージとは別に開発および配置できますが、スクリプト ソリューションを更新する場合は、パッケージ全体を再配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="de373-111">Custom objects can be developed and deployed separately from the parent package, whereas an update made to a scripting solution requires the redeployment of the whole package.</span></span>  
  
<span data-ttu-id="de373-112">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="de373-112">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="de373-113">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="de373-113">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="de373-114">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="de373-114">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="de373-115">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="de373-115">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de373-116">参照</span><span class="sxs-lookup"><span data-stu-id="de373-116">See Also</span></span>  
 [<span data-ttu-id="de373-117">カスタム オブジェクトを使用したパッケージの拡張</span><span class="sxs-lookup"><span data-stu-id="de373-117">Extending Packages with Custom Objects</span></span>](../extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
  
  

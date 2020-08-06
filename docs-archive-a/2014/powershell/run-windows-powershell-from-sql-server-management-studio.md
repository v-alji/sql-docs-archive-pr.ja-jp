---
title: SQL Server Management Studio から Windows PowerShell を実行する方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 1f841825-da1f-4062-9a81-3cdbab03845b
author: stevestein
ms.author: sstein
ms.openlocfilehash: e0330e833aaa3344416a31aa700a2b1f6bb4a6e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640113"
---
# <a name="run-windows-powershell-from-sql-server-management-studio"></a><span data-ttu-id="ba18d-102">SQL Server Management Studio から Windows PowerShell を実行する方法</span><span class="sxs-lookup"><span data-stu-id="ba18d-102">Run Windows PowerShell from SQL Server Management Studio</span></span>
  <span data-ttu-id="ba18d-103">Windows PowerShell セッションは、 **の** オブジェクト エクスプローラー [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]から起動できます。</span><span class="sxs-lookup"><span data-stu-id="ba18d-103">You can start Windows PowerShell sessions from **Object Explorer** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]<span data-ttu-id="ba18d-104">Windows PowerShell を起動し、モジュールを読み込み、 `sqlps` **オブジェクトエクスプローラー**ツリー内の関連付けられているノードにパスコンテキストを設定します。</span><span class="sxs-lookup"><span data-stu-id="ba18d-104">launches Windows PowerShell, loads the `sqlps` module, and sets the path context to the associated node in the **Object Explorer** tree.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="ba18d-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="ba18d-105">Before You Begin</span></span>  
 <span data-ttu-id="ba18d-106">**オブジェクトエクスプローラー**のオブジェクトに対して powershell の実行を指定すると、は、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] powershell スナップインが読み込まれて登録された Windows powershell セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="ba18d-106">When you specify running PowerShell for an object in **Object Explorer**, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] starts a Windows PowerShell session in which the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell snap-ins have been loaded and registered.</span></span> <span data-ttu-id="ba18d-107">セッションのパスは、オブジェクト エクスプローラーで右クリックしたオブジェクトの場所にあらかじめ設定されています。</span><span class="sxs-lookup"><span data-stu-id="ba18d-107">The path for the session is preset to the location of the object you right clicked in Object Explorer.</span></span> <span data-ttu-id="ba18d-108">たとえば、オブジェクト エクスプローラーで [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベース オブジェクトを右クリックして **[PowerShell の起動]** を選択した場合、Windows PowerShell パスは次のように設定されます。</span><span class="sxs-lookup"><span data-stu-id="ba18d-108">For example, if you right-click the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database object in Object Explorer and select **Start PowerShell**, the Windows PowerShell path is set to the following:</span></span>  
  
```
SQLSERVER:\SQL\MyComputer\MyInstance\Databases\AdventureWorks2012>  
```  
  
## <a name="to-run-powershell-from-sql-server-management-studio"></a><span data-ttu-id="ba18d-109">SQL Server Management Studio から PowerShell を実行するには</span><span class="sxs-lookup"><span data-stu-id="ba18d-109">To run PowerShell from SQL Server Management Studio</span></span> 
  
1.  <span data-ttu-id="ba18d-110">**オブジェクトエクスプローラー**を開きます。</span><span class="sxs-lookup"><span data-stu-id="ba18d-110">Open **Object Explorer**.</span></span>  
  
2.  <span data-ttu-id="ba18d-111">作業対象オブジェクトのノードに移動します。</span><span class="sxs-lookup"><span data-stu-id="ba18d-111">Navigate to the node for the object to be worked on.</span></span>  
  
3.  <span data-ttu-id="ba18d-112">オブジェクトを右クリックし、 **[PowerShell の起動]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ba18d-112">Right-click the object and select **Start PowerShell**.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="ba18d-113">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="ba18d-113">Permissions</span></span>  
 <span data-ttu-id="ba18d-114">PowerShell を [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]で開いた場合は管理者特権で実行されないため、WMI の呼び出しなどの一部のアクティビティが実行されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="ba18d-114">When opened from [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], PowerShell does not run with Administrator privileges which may prevent some activities such as calls to WMI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba18d-115">参照</span><span class="sxs-lookup"><span data-stu-id="ba18d-115">See Also</span></span>  
 [<span data-ttu-id="ba18d-116">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="ba18d-116">SQL Server PowerShell</span></span>](sql-server-powershell.md)  

---
title: パッケージを削除する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 85b7d512-0ea7-47f5-8937-b1af6592b5b5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5c7a61d8c65c1934eb72101bf91ac3b73be60f94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743393"
---
# <a name="delete-packages"></a><span data-ttu-id="2da68-102">パッケージを削除する</span><span class="sxs-lookup"><span data-stu-id="2da68-102">Delete Packages</span></span>
  <span data-ttu-id="2da68-103">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]では、ファイル システムに保存したパッケージを削除できます。</span><span class="sxs-lookup"><span data-stu-id="2da68-103">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], you can delete packages saved to the file system.</span></span> <span data-ttu-id="2da68-104">パッケージを削除した場合は完全に削除されるため、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトに復元することはできません。</span><span class="sxs-lookup"><span data-stu-id="2da68-104">If you delete a package, it is deleted permanently and it cannot be restored to an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2da68-105">パッケージを [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトから削除しても、他のプロジェクトでそのパッケージを使用する場合は、 **[削除]** オプションではなく、 **[プロジェクトから削除]** オプションを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2da68-105">If you want to remove packages from an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, but use them in other projects, then you should use the **Exclude From Project** option instead of the **Delete** option.</span></span>  
  
### <a name="to-delete-a-package-in-business-intelligence"></a><span data-ttu-id="2da68-106">Business Intelligence でパッケージを削除するには</span><span class="sxs-lookup"><span data-stu-id="2da68-106">To delete a package in Business Intelligence</span></span>  
  
1.  <span data-ttu-id="2da68-107">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、削除するパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="2da68-107">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want to delete.</span></span>  
  
2.  <span data-ttu-id="2da68-108">ソリューション エクスプローラーでパッケージを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2da68-108">In Solution Explorer, right-click the package, and then click **Delete**.</span></span>  
  
3.  <span data-ttu-id="2da68-109">削除を確認するには **[OK]** を、パッケージを削除せずに残すには **[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2da68-109">Click **OK** to confirm the deletion or click **Cancel** to keep the package.</span></span>  
  
  

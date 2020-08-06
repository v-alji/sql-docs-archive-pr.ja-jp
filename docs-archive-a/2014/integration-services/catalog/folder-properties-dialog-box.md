---
title: '[フォルダーのプロパティ] ダイアログ ボックス | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.iscreatefolder.f1
- sql12.ssis.ssms.isfolderprop.general.f1
- sql12.ssis.ssms.isfolderprop.permissions.f1
ms.assetid: d9a2bfae-fcc8-46be-b588-4a9db03f7e45
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4075a429f94451d7b00ee44ac1ac799c29787a41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642248"
---
# <a name="folder-properties-dialog-box"></a><span data-ttu-id="9c2d4-102">[フォルダーのプロパティ] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="9c2d4-102">Folder Properties Dialog Box</span></span>
  <span data-ttu-id="9c2d4-103">フォルダーには、`SSISDB` カタログ内のプロジェクトおよび環境が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9c2d4-103">A folder contains projects and environments in the `SSISDB` catalog.</span></span> <span data-ttu-id="9c2d4-104">フォルダーごとに、フォルダーの内容に適用される権限を定義します。</span><span class="sxs-lookup"><span data-stu-id="9c2d4-104">Each folder defines permissions that apply to the contents of the folder.</span></span> <span data-ttu-id="9c2d4-105">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の権限の詳細については、「[catalog.grant_permission &#40;SSISDB データベース&#41;](/sql/integration-services/system-stored-procedures/catalog-grant-permission-ssisdb-database)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9c2d4-105">For more information about [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] permissions, see [catalog.grant_permission &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-grant-permission-ssisdb-database).</span></span>  
  
## <a name="to-set-folder-description-and-permissions"></a><span data-ttu-id="9c2d4-106">フォルダーの説明と権限を設定するには</span><span class="sxs-lookup"><span data-stu-id="9c2d4-106">To Set Folder Description and Permissions</span></span>  
  
1.  <span data-ttu-id="9c2d4-107">フォルダーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9c2d4-107">Right-click the folder and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="9c2d4-108">**[全般]** ページで、 **[全般]** の下にある **[説明]** を選択して説明を入力します (省略可)。</span><span class="sxs-lookup"><span data-stu-id="9c2d4-108">On the **General** page, select **Description** under **General** and enter an optional description.</span></span>  
  
3.  <span data-ttu-id="9c2d4-109">**[権限]** ページで、 **[参照]** をクリックし、1 つ以上のデータベース プリンシパルを選択して **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9c2d4-109">On the **Permissions** page, click **Browse...**, select one or more database principals, and click **OK**.</span></span>  
  
4.  <span data-ttu-id="9c2d4-110">**[ログインまたはロール]** で名前を選択し、 **[権限]** で適切な権限を指定します。</span><span class="sxs-lookup"><span data-stu-id="9c2d4-110">Select a name under **Logins or roles** and specify the appropriate permissions under **Permissions**.</span></span>  
  
5.  <span data-ttu-id="9c2d4-111">**[OK]** をクリックして変更を受け入れ、 **[フォルダーのプロパティ]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="9c2d4-111">Click **OK** to accept the changes and close the **Folders Properties** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c2d4-112">参照</span><span class="sxs-lookup"><span data-stu-id="9c2d4-112">See Also</span></span>  
 <span data-ttu-id="9c2d4-113">[Integration Services &#40;SSIS&#41; サーバー](integration-services-ssis-server-and-catalog.md) </span><span class="sxs-lookup"><span data-stu-id="9c2d4-113">[Integration Services &#40;SSIS&#41; Server](integration-services-ssis-server-and-catalog.md) </span></span>  
 [<span data-ttu-id="9c2d4-114">catalog.grant_permission &#40;SSISDB データベース&#41;</span><span class="sxs-lookup"><span data-stu-id="9c2d4-114">catalog.grant_permission &#40;SSISDB Database&#41;</span></span>](/sql/integration-services/system-stored-procedures/catalog-grant-permission-ssisdb-database)  
  
  

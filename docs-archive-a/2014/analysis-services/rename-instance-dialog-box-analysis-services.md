---
title: '[インスタンス名の変更] ダイアログボックス (Analysis Services) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.ssas.instancerename.f1
ms.assetid: 3708d992-8dd9-461c-8aa0-5da6df96ed70
author: minewiskan
ms.author: owend
ms.openlocfilehash: 69d30a75f07197abce7990f6c55299a6064969db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644156"
---
# <a name="rename-instance-dialog-box-analysis-services"></a><span data-ttu-id="4e760-102">[インスタンス名の変更] ダイアログ ボックス (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="4e760-102">Rename Instance Dialog Box (Analysis Services)</span></span>
  <span data-ttu-id="4e760-103">**[インスタンス名の変更]** ダイアログ ボックスを使用すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]の既存のインスタンスの名前を変更できます。</span><span class="sxs-lookup"><span data-stu-id="4e760-103">Use the **Rename Instance** dialog box to rename an existing instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="4e760-104">**[インスタンス名の変更]** ダイアログ ボックスを表示するには、C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE から **インスタンス名の変更** ツール (asinstancerename.exe) を起動します。</span><span class="sxs-lookup"><span data-stu-id="4e760-104">You can display the **Rename Instance** dialog box by launching the **Instance Rename** tool (asinstancerename.exe) from C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4e760-105">Options</span><span class="sxs-lookup"><span data-stu-id="4e760-105">Options</span></span>  
  
|<span data-ttu-id="4e760-106">期間</span><span class="sxs-lookup"><span data-stu-id="4e760-106">Term</span></span>|<span data-ttu-id="4e760-107">定義</span><span class="sxs-lookup"><span data-stu-id="4e760-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="4e760-108">**[名前を変更するインスタンス]**</span><span class="sxs-lookup"><span data-stu-id="4e760-108">**Instance to rename**</span></span>|<span data-ttu-id="4e760-109">名前を変更するインスタンスを選択します。</span><span class="sxs-lookup"><span data-stu-id="4e760-109">Select the instance to be renamed.</span></span>|  
|<span data-ttu-id="4e760-110">**[新しいインスタンス名]**</span><span class="sxs-lookup"><span data-stu-id="4e760-110">**New instance name**</span></span>|<span data-ttu-id="4e760-111">インスタンスの新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="4e760-111">Type the desired instance name.</span></span> <span data-ttu-id="4e760-112">サーバー名は含めないでください。</span><span class="sxs-lookup"><span data-stu-id="4e760-112">Do not include the server name.</span></span> <span data-ttu-id="4e760-113">つまり、 \<server name> \\<インスタンス名を入力する代わりに、「 \> 」と入力し \<instance name> ます。</span><span class="sxs-lookup"><span data-stu-id="4e760-113">That is, instead of entering \<server name>\\<instance name\>, enter only \<instance name>.</span></span><br /><br /> <span data-ttu-id="4e760-114">名前を変更するインスタンスを既定の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスにする場合は、空白のままにします。</span><span class="sxs-lookup"><span data-stu-id="4e760-114">If you want the instance you are renaming to be the default [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance, leave the name blank.</span></span>|  
|<span data-ttu-id="4e760-115">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="4e760-115">**Username**</span></span>|<span data-ttu-id="4e760-116">サービスの開始時に使用されるアカウントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4e760-116">Shows the account the service will use to start.</span></span> <span data-ttu-id="4e760-117">ユーザー名は変更できません。</span><span class="sxs-lookup"><span data-stu-id="4e760-117">The user name cannot be changed.</span></span>|  
|<span data-ttu-id="4e760-118">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="4e760-118">**Password**</span></span>|<span data-ttu-id="4e760-119">サービス アカウントのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="4e760-119">Type the password of the service account.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4e760-120">参照</span><span class="sxs-lookup"><span data-stu-id="4e760-120">See Also</span></span>  
 [<span data-ttu-id="4e760-121">多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;</span><span class="sxs-lookup"><span data-stu-id="4e760-121">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  

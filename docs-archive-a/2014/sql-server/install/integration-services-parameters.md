---
title: Integration Services Parameters |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, parameters
ms.assetid: b1bb3ea3-8097-4e76-b9c2-78a0f46a23bc
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 76a5ebe7018fdc58f02a4d2454d40f172c752c4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740726"
---
# <a name="integration-services-parameters"></a><span data-ttu-id="7df32-102">Integration Services パラメーター</span><span class="sxs-lookup"><span data-stu-id="7df32-102">Integration Services Parameters</span></span>
  <span data-ttu-id="7df32-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] では、コンピューター上のパッケージを分析するか、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ファイルシステム内のパッケージファイルを分析するかを決定できます。</span><span class="sxs-lookup"><span data-stu-id="7df32-103">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], you can decide to analyze [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages on the computer, or [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package files in the file system.</span></span> <span data-ttu-id="7df32-104">ファイル システムのファイルを分析する場合は、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを含むフォルダーのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="7df32-104">If you analyze files in the file system, provide a path to the folder that contains the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7df32-105">Options</span><span class="sxs-lookup"><span data-stu-id="7df32-105">Options</span></span>  
 <span data-ttu-id="7df32-106">**[コンピューターの SSIS パッケージを分析する]**</span><span class="sxs-lookup"><span data-stu-id="7df32-106">**Analyze SSIS packages on Computer**</span></span>  
 <span data-ttu-id="7df32-107">コンピューター上の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを分析するときは、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="7df32-107">Select this option to analyze [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages on the computer.</span></span> <span data-ttu-id="7df32-108">既定では、このオプションが選択されています。</span><span class="sxs-lookup"><span data-stu-id="7df32-108">By default, this option is selected.</span></span>  
  
 <span data-ttu-id="7df32-109">**[SSIS パッケージ ファイルを分析する]**</span><span class="sxs-lookup"><span data-stu-id="7df32-109">**Analyze SSIS package files**</span></span>  
 <span data-ttu-id="7df32-110">ファイル システムの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを分析するときは、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="7df32-110">Select this option to analyze [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages in the file system.</span></span>  
  
 <span data-ttu-id="7df32-111">**[SSIS パッケージのパス]**</span><span class="sxs-lookup"><span data-stu-id="7df32-111">**Path to SSIS packages**</span></span>  
 <span data-ttu-id="7df32-112">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージが保存されている UNC またはローカル パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="7df32-112">Locate a UNC or local path that holds your [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="7df32-113">ファイル名を含める必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7df32-113">You do not have to include file names.</span></span> <span data-ttu-id="7df32-114">入力したパスにアクセスできない場合は、[**次へ**] をクリックすることはできません。</span><span class="sxs-lookup"><span data-stu-id="7df32-114">If the path you have entered cannot be accessed, you cannot click **Next**.</span></span> <span data-ttu-id="7df32-115">既定では、パスは空白です。</span><span class="sxs-lookup"><span data-stu-id="7df32-115">By default, the path is blank.</span></span> <span data-ttu-id="7df32-116">このフィールドは、[ **SSIS パッケージファイルの分析**] を選択した場合にのみ有効になります。</span><span class="sxs-lookup"><span data-stu-id="7df32-116">This field is enabled only when you select **Analyze SSIS package files**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7df32-117">参照</span><span class="sxs-lookup"><span data-stu-id="7df32-117">See Also</span></span>  
 <span data-ttu-id="7df32-118">[アップグレードアドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="7df32-118">[Working with Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="7df32-119">アップグレード アドバイザーのユーザー インターフェイス リファレンス</span><span class="sxs-lookup"><span data-stu-id="7df32-119">Upgrade Advisor User Interface Reference</span></span>](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  

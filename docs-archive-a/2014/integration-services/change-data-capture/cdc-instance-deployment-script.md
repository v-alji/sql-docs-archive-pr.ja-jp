---
title: '[CDC インスタンス配置スクリプト] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 8fa82822-ac99-48ef-a18d-f4f3a77105b4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6deea884168c2329e312eeaa2be16c28a955cca3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741198"
---
# <a name="cdc-instance-deployment-script"></a><span data-ttu-id="37bbe-102">[CDC インスタンス配置スクリプト]</span><span class="sxs-lookup"><span data-stu-id="37bbe-102">CDC Instance Deployment Script</span></span>
  <span data-ttu-id="37bbe-103">CCD インスタンス配置スクリプトを表示する [CDC インスタンス配置スクリプト] ダイアログ ボックスです。</span><span class="sxs-lookup"><span data-stu-id="37bbe-103">The CDC Instance Deployment Script dialog box that displays the CDC instance deployment script.</span></span> <span data-ttu-id="37bbe-104">このスクリプトは、すべてのアーティファクトが異なる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにある CDC データベースを再作成するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="37bbe-104">This script can be used to re-create the CDC database with all of its artifacts on a different [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="37bbe-105">配置スクリプトの終了時に、次のことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37bbe-105">At the completion of the deployment script, you should make sure of the following:</span></span>  
  
-   <span data-ttu-id="37bbe-106">配置スクリプトでは、Oracle CDC Service 構成コンソールを使用することにより、またはプログラムが作成する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 準備スクリプト **を使用することにより、ターゲットの** インスタンスが Oracle CDC に対して準備されたと仮定します。</span><span class="sxs-lookup"><span data-stu-id="37bbe-106">The deployment script assumes that the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance was prepared for Oracle CDC, by using the Oracle CDC Service Configuration Console or by using **prepare script** that program creates.</span></span>  
  
-   <span data-ttu-id="37bbe-107">スクリプトのうち、CDC に対してデータベースを有効にするために使用される部分は、 `sysadmin`によって実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37bbe-107">The part of the script that is used to enable the database for CDC needs to be run by a `sysadmin`.</span></span>  
  
-   <span data-ttu-id="37bbe-108">スクリプトでは、Oracle のログ マイニング パスワードは保持されません。</span><span class="sxs-lookup"><span data-stu-id="37bbe-108">The script does not preserve the Oracle log-mining password.</span></span> <span data-ttu-id="37bbe-109">このパスワードは、スクリプトが実行され、Oracle CDC Service が開始された後に、手動で設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37bbe-109">This needs to be set manually after the script is run and the Oracle CDC Service is started.</span></span>  
  
 <span data-ttu-id="37bbe-110">**[CDC インスタンス配置スクリプト]** ダイアログ ボックスで次のオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="37bbe-110">Select the following options in the **CDC Instance Deployment Script** dialog box.</span></span>  
  
 <span data-ttu-id="37bbe-111">**[名前を付けて保存]**</span><span class="sxs-lookup"><span data-stu-id="37bbe-111">**Save As**</span></span>  
 <span data-ttu-id="37bbe-112">任意の場所に保存できるテキスト ファイルにスクリプトを保存します。</span><span class="sxs-lookup"><span data-stu-id="37bbe-112">Saves the script in a text file that you can save in any location you want.</span></span> <span data-ttu-id="37bbe-113">スクリプトを含むファイルを他の任意のサーバーにコピーして、そのサーバーで実行できます。</span><span class="sxs-lookup"><span data-stu-id="37bbe-113">You can copy the file with the script to any other server to run it there.</span></span>  
  
 <span data-ttu-id="37bbe-114">**Copy** に設定する必要があります</span><span class="sxs-lookup"><span data-stu-id="37bbe-114">**Copy**</span></span>  
 <span data-ttu-id="37bbe-115">スクリプトをクリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="37bbe-115">Copies the script to the clipboard.</span></span> <span data-ttu-id="37bbe-116">その後、スクリプトを [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または任意のテキスト エディターに貼り付けて、後でスクリプトを実行できます。</span><span class="sxs-lookup"><span data-stu-id="37bbe-116">You can then paste the script into the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or any text editor to run the scripts later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37bbe-117">参照</span><span class="sxs-lookup"><span data-stu-id="37bbe-117">See Also</span></span>  
 [<span data-ttu-id="37bbe-118">CDC 用の SQL Server の準備</span><span class="sxs-lookup"><span data-stu-id="37bbe-118">Prepare SQL Server for CDC</span></span>](prepare-sql-server-for-cdc.md)  
  
  

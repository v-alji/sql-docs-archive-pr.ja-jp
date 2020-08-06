---
title: Oracle データベースのプロパティの編集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- oraProp
ms.assetid: 58dc99f1-ee6b-4508-bb66-2bc589611ff7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d3cad2735e6cd6095f9730f3b4e7228526451d34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634595"
---
# <a name="edit-the-oracle-database-properties"></a><span data-ttu-id="5f8ff-102">Oracle データベースのプロパティの編集</span><span class="sxs-lookup"><span data-stu-id="5f8ff-102">Edit the Oracle Database Properties</span></span>
  <span data-ttu-id="5f8ff-103">プロパティ エディターの [Oracle] タブを使用して、新しいインスタンス ウィザードの [CDC データベースの作成] ページで指定した説明を変更し、Oracle ログ マイニング データベースの接続情報を変更します。</span><span class="sxs-lookup"><span data-stu-id="5f8ff-103">Use the Oracle tab in the Properties editor to make changes to the description you provided in the Create CDC database page in the New Instance wizard and to make changes to the Oracle Log Mining database connection information.</span></span>  
  
 <span data-ttu-id="5f8ff-104">**[Oracle]** タブの情報について、次に説明します。</span><span class="sxs-lookup"><span data-stu-id="5f8ff-104">The following describes the information in the **Oracle** tab.</span></span>  
  
 <span data-ttu-id="5f8ff-105">**Name**</span><span class="sxs-lookup"><span data-stu-id="5f8ff-105">**Name**</span></span>  
 <span data-ttu-id="5f8ff-106">新しいインスタンス ウィザードの [CDC データベースの作成] ページで入力した CDC インスタンスの名前です。</span><span class="sxs-lookup"><span data-stu-id="5f8ff-106">The name of the CDC Instance that you entered in the Create CDC Database page in the New Instance wizard.</span></span> <span data-ttu-id="5f8ff-107">このフィールドは読み取り専用であり、この情報を編集することはできません。</span><span class="sxs-lookup"><span data-stu-id="5f8ff-107">This field is read only and you cannot edit this information.</span></span>  
  
 <span data-ttu-id="5f8ff-108">**説明**</span><span class="sxs-lookup"><span data-stu-id="5f8ff-108">**Description**</span></span>  
 <span data-ttu-id="5f8ff-109">新しいインスタンスの説明を編集するか、CDC インスタンスの作成時に説明を追加しなかった場合は説明を追加できます。</span><span class="sxs-lookup"><span data-stu-id="5f8ff-109">You can edit the description of the new instance or add one if you did not do so when creating the CDC Instance.</span></span>  
  
 <span data-ttu-id="5f8ff-110">**[Oracle 接続文字列]**</span><span class="sxs-lookup"><span data-stu-id="5f8ff-110">**Oracle Connect String**</span></span>  
 <span data-ttu-id="5f8ff-111">使用している Oracle データベースがあるコンピューターへの Oracle 接続文字列です。</span><span class="sxs-lookup"><span data-stu-id="5f8ff-111">The Oracle connect string to the computer with the Oracle database you are using.</span></span> <span data-ttu-id="5f8ff-112">このフィールドは読み取り専用であり、この情報を編集することはできません。</span><span class="sxs-lookup"><span data-stu-id="5f8ff-112">This field is read only and you cannot edit this information.</span></span> <span data-ttu-id="5f8ff-113">これは、接続文字列を変更すると、Oracle CDC インスタンスがまったく別の Oracle データベースを指定し、 **cdc.xdbcdc_config** テーブルに格納された CDC インスタンスの状態が破損することがあるためです。</span><span class="sxs-lookup"><span data-stu-id="5f8ff-113">This is because some changes to the connect string may point the Oracle CDC Instance to another Oracle database entirely, corrupting the CDC Instance state as stored in the **cdc.xdbcdc_config** table.</span></span> <span data-ttu-id="5f8ff-114">小規模な変更が必要な場合は、SQL Server Management Studio を使用して、接続文字列を構成テーブルで直接変更できます。</span><span class="sxs-lookup"><span data-stu-id="5f8ff-114">If minor changes are needed, you can change the connect string directly in the configuration table using SQL Server Management Studio.</span></span>  
  
 <span data-ttu-id="5f8ff-115">**[Oracle ログ マイニング認証]**</span><span class="sxs-lookup"><span data-stu-id="5f8ff-115">**Oracle Log Mining Authentication**</span></span>  
 <span data-ttu-id="5f8ff-116">ログ マイナーを含む Oracle データベースの認証資格情報を入力するには、 **[認証]** で次のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="5f8ff-116">To enter the authentication credentials for the Oracle database that contains the log miner, select one of the following under **Authentication**:</span></span>  
  
-   <span data-ttu-id="5f8ff-117">**[Windows 認証]** : 現在の Windows ドメイン資格情報を使用する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="5f8ff-117">**Windows Authentication**: Select this to use the current Windows domain credentials.</span></span> <span data-ttu-id="5f8ff-118">このオプションは、Oracle データベースが Windows 認証と連動するように構成されている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="5f8ff-118">You can use this option only if the Oracle database is configured to work with Windows authentication.</span></span>  
  
-   <span data-ttu-id="5f8ff-119">**[Oracle 認証]** : このオプションを選択する場合、接続先の Oracle データベースのユーザーの **[ユーザー名]** と **[パスワード]** を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f8ff-119">**Oracle Authentication**: If you select this option, you must type the **User Name** and **Password** for the user in the Oracle database you are connecting to.</span></span>  
  
 <span data-ttu-id="5f8ff-120">Oracle データベースのプロパティは、ビューアーで表示できます。</span><span class="sxs-lookup"><span data-stu-id="5f8ff-120">You can view the Oracle database properties in the viewer.</span></span> <span data-ttu-id="5f8ff-121">ビューアーを使用する場合、情報は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="5f8ff-121">When using the viewer the information is read only.</span></span> <span data-ttu-id="5f8ff-122">ビューアーには、テーブルのキャプチャ対象列の一覧も含まれています。</span><span class="sxs-lookup"><span data-stu-id="5f8ff-122">The viewer also includes a list of the captured columns in the table.</span></span> <span data-ttu-id="5f8ff-123">ビューアーへのアクセス方法については、「 [How to Manage a CDC Instance](manage-a-cdc-instance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f8ff-123">For information on how to access the viewer, see [How to Manage a CDC Instance](manage-a-cdc-instance.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f8ff-124">参照</span><span class="sxs-lookup"><span data-stu-id="5f8ff-124">See Also</span></span>  
 <span data-ttu-id="5f8ff-125">[CDC デザイナー コンソールから CDC サービスを管理する方法](how-to-manage-a-cdc-service-from-the-cdc-designer-console.md) </span><span class="sxs-lookup"><span data-stu-id="5f8ff-125">[How to Manage a CDC Service from the CDC Designer Console](how-to-manage-a-cdc-service-from-the-cdc-designer-console.md) </span></span>  
 <span data-ttu-id="5f8ff-126">[Oracle ソース データベースへの接続](connect-to-an-oracle-source-database.md) </span><span class="sxs-lookup"><span data-stu-id="5f8ff-126">[Connect to an Oracle Source Database](connect-to-an-oracle-source-database.md) </span></span>  
 [<span data-ttu-id="5f8ff-127">Oracle への接続</span><span class="sxs-lookup"><span data-stu-id="5f8ff-127">Connect to Oracle</span></span>](connect-to-oracle.md)  
  
  

---
Type: Project
tags: [projects/00-💰-Sell-Old-Products]
Status: 🟡 New
Short Description:
Date Started: 2023-12-01 10:20
---

> 🌟 **Embrace the Challenge:** 
> This project is your opportunity to transform aspirations into reality. Embark on a journey of growth and discovery, where your skills and determination converge to achieve meaningful goals.

- [x] Project: 00 💰 Sell Old Products 🛫 2023-12-01 10:20 📅 2023-12-31 ✅ 2023-12-31
- [ ]  Project: 00 💰 Sell Old Products  Part 2 🛫 2024-01-01 10:20 📅 2024-01-15 ✅ 2023-12-31
## 🎯 **Goals**
[💡^]: Remember to set [[S.M.A.R.T]] goals
[💡^]: Use the [[5 Whys Technique - Root Cause Analysis]]

- To Sell item that I no longer use so people could benefit from them at a lower price.
## ✅ **Tasks**

- [x] Review Excel created by marie anne ✅ 2023-12-12
- [x] define prices for each item ✅ 2023-12-14
	- [x] [[Price for ps4 slim]] ✅ 2023-12-06
		- [x] Mercadolibre ✅ 2023-12-06
		- [x] Marketplace ⏫ 📅 2023-12-10 ✅ 2023-12-12
	- [x] Price for Beds ✅ 2023-12-14
	- [x] Price For baby bed 📅 2023-12-14 ✅ 2023-12-14
		- [x] Update sizing, photos and pricing ✅ 2023-12-14
- [x] list of possible website to sell items ✅ 2023-12-12
	- mercadolibre
	- marketplace
- [ ] finish [docs.google.com/spreadsheets/d/1GxaP155dADXKbDVmAjyudKv7t8xph0E3/edit#gid=1550613623](https://docs.google.com/spreadsheets/d/1GxaP155dADXKbDVmAjyudKv7t8xph0E3/edit#gid=1550613623)
	- [ ] Take new photos of table with chairs wood
	- [ ] upload new listing of only wood table with new photos
	- [ ] Colchon sizing
- [ ] New Listings-
	- [ ] Baby trash can
	- [ ] Create a listing for each bed
	- [ ] Create a listing for bed table one for each
	- [ ] Create a listing for a massage bed
	- [ ] Listing for nest café machine
	- [ ] listing for PC parts
	- [ ] listing for violin
	- [ ] listing for L table
	- [ ] couch  white 
	- [ ] puff white
	- [ ] houses

---
## 📖 Journal Insights
[💭^]: Reflect on your progress, challenges, and inspirations throughout the project. Use this space to capture your thoughts, ideas, and emotions.

``` dataview
LIST item.text
FROM "0. Daybook"
FLATTEN file.lists as item
WHERE contains(item.tags, this.file.tags[0])

```

## 🗒 Notes
[💭^]: Gather relevant information, resources, and insights from other notes related to this project.
``` dataview
LIST 
WHERE file.name != this.file.name 
and  contains(file.folder, this.file.folder)
```


## 🤝 Related Projects
[💭^]: Explore connections and synergies between this project and other ongoing ventures. Identify opportunities for collaboration and knowledge sharing.
``` dataview
LIST 
FROM "1. Projects"
AND "2. Areas"
WHERE contains(file.tags,this.file.tags[0]) and file.name != this.file.name
```

## 📚 Resources
[💭^]: Compile a list of helpful tools, articles, tutorials, and external resources that can support your project's success.
``` dataview
LIST 
FROM "3. Resources"
WHERE contains(file.tags,this.file.tags[0])
```


---
**Remember:**

- **Believe in yourself:** Your potential is limitless. Embrace your abilities and trust in your capacity to achieve great things.

- **Enjoy the journey:** Learning and growth are inherent parts of any project. Embrace the challenges, celebrate the victories, and savor the entire experience.

**Embrace the excitement and embark on your journey of accomplishment!**

> [!quote] When something is important enough, you do it even if the odds are not in your favor.
> — Elon Musk

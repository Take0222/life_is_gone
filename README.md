# life_is_gone
import matplotlib.pyplot as plt

# Prepare the data
options = ["Pattern 1: NZ WH & ASU Grad School", 
           "Pattern 2: Domestic Grad School", 
           "Pattern 3: Employment", 
           "Pattern 4: 1-Year Prep & Pattern 1"]
benefits = [("International experience", "English improvement", "Career prep in US"),
            ("Stay with girlfriend", "Career prep in Japan", "Utilize existing network"),
            ("Financial stability", "Early work experience", "Potential same location with girlfriend"),
            ("Adequate prep", "Planned career/education path", "Time with girlfriend")]
drawbacks = [("Income instability during WH", "Temporary separation from girlfriend"),
             ("Lack of international experience", "Delayed US career prep"),
             ("Reduced learning opportunities", "Misalignment with US career goal"),
             ("Delayed career/education start", "Progress dependent on prep period")]

fig, axes = plt.subplots(len(options), 1, figsize=(12, 15), constrained_layout=True)

# Plot each option
for i, (option, benefit, drawback) in enumerate(zip(options, benefits, drawbacks)):
    axes[i].set_title(option, fontsize=14, fontweight='bold')
    axes[i].barh(['Benefits', 'Drawbacks'], [len(benefit), len(drawback)], color=['green', 'red'])
    
    for j, b in enumerate(benefit):
        axes[i].text(0.1, j - 0.1, b, ha='left', va='center', color='green')
    for k, d in enumerate(drawback):
        axes[i].text(len(benefit) - 0.5, k - 0.1, d, ha='left', va='center', color='red')

    axes[i].set_xlim(0, max(len(benefit), len(drawback)) + 1)
    axes[i].set_yticks([])

plt.suptitle('Career Path Options: Benefits and Drawbacks', fontsize=16, fontweight='bold')
plt.show()

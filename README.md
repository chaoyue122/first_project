# first_project
Data Processing and Visualization
import pandas as pd
data=pd.read_csv(r'C:\Users\21196\Desktop\try.csv')
data.columns.tolist()
high_cond = data[data["ionic_conductivity"] > 1e-4]
print("\n筛选结果（电导率 > 1e-4 S/cm）：")
print(high_cond[["formula", "ionic_conductivity"]].sort_values(by="ionic_conductivity", ascending=False))
import matplotlib.pyplot as plt
plt.rcParams["figure.dpi"] = 300
plt.hist(data["ionic_conductivity"], bins=20, log=True, alpha=0.7, color='skyblue')
# 添加筛选阈值线
plt.axvline(x=1e-4, color='red', linestyle='--', label=' Screening threshold(1e-4 S/cm)')
# 添加标签和标题
plt.xlabel("Ionic_Conductivity (S/cm)")
plt.ylabel("Count")
plt.title("Distribution of Li-ion Couductor")
plt.grid(True, linestyle='--', alpha=0.5)
# 显示图例和图表
plt.legend()
plt.show()


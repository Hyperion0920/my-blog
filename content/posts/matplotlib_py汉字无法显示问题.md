# 1. 卸载系统级 matplotlib（如使用 apt 安装）
sudo apt remove python3-matplotlib

# 2. 使用 pip 安装到用户目录（推荐）
pip install --user matplotlib

# 3. 重新安装 mplfonts
pip install --user --force-reinstall mplfonts

# 4. 初始化
~/.local/bin/mplfonts init

# 5. 检查字体是否安装成功（没安装字体，安装即可）
import matplotlib.font_manager as fm

 #检查 WenQuanYi Zen Hei 是否被识别
font_paths = fm.findSystemFonts()
found = [p for p in font_paths if 'zenhei' in p.lower()]
if found:
    print("✓ 字体已安装:", found[0])
    print("  字体名称:", fm.FontProperties(fname=found[0]).get_name())
else:
    print("✗ 未找到字体，请确认 fonts-wqy-zenhei 是否安装成功")

# 6. 清除缓存
rm -rf ~/.cache/matplotlib/*
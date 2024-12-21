using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace WindowsFormsApp1
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
            InitializeCustomComponents();
        }

        private void InitializeCustomComponents()
        {
            // Настройка размеров формы
            this.Text = "Продукция - Управление";
            this.Size = new Size(1100, 650);
            this.StartPosition = FormStartPosition.CenterScreen;

            // Верхняя панель для управления
            Panel topPanel = new Panel
            {
                Dock = DockStyle.Top,
                Height = 100,
                BackColor = Color.LightGray,
                Padding = new Padding(10)
            };

            // Панель фильтров и поиска
            GroupBox filterGroup = new GroupBox
            {
                Text = "Фильтры и поиск",
                Dock = DockStyle.Left,
                Width = 400,
                Padding = new Padding(10)
            };

            // Сортировка
            Label lblSort = new Label { Text = "Сортировка:", AutoSize = true, Location = new Point(10, 25) };
            ComboBox cbSort = new ComboBox
            {
                Width = 180,
                Location = new Point(10, 45),
                DropDownStyle = ComboBoxStyle.DropDownList,
                Name = "cbSort"
            };
            cbSort.Items.AddRange(new string[] { "Наименование", "Цех", "Минимальная стоимость" });

            // Фильтрация
            Label lblFilter = new Label { Text = "Фильтр по типу:", AutoSize = true, Location = new Point(210, 25) };
            ComboBox cbFilter = new ComboBox
            {
                Width = 180,
                Location = new Point(210, 45),
                DropDownStyle = ComboBoxStyle.DropDownList,
                Name = "cbFilter"
            };
            cbFilter.Items.Add("Все типы");

            // Добавление элементов в панель фильтров
            filterGroup.Controls.Add(lblSort);
            filterGroup.Controls.Add(cbSort);
            filterGroup.Controls.Add(lblFilter);
            filterGroup.Controls.Add(cbFilter);

            // Поиск
            Label lblSearch = new Label { Text = "Поиск:", AutoSize = true, Location = new Point(10, 20) };
            TextBox txtSearch = new TextBox
            {
                Width = 200,
                Location = new Point(60, 15),
                Name = "txtSearch"
            };

            // Добавление поиска на верхнюю панель
            topPanel.Controls.Add(lblSearch);
            topPanel.Controls.Add(txtSearch);
            topPanel.Controls.Add(filterGroup);

            // Центральная таблица (DataGridView)
            DataGridView dgvProducts = new DataGridView
            {
                Dock = DockStyle.Fill,
                ReadOnly = true,
                MultiSelect = true,
                Name = "dgvProducts",
                AllowUserToAddRows = false,
                AutoSizeColumnsMode = DataGridViewAutoSizeColumnsMode.Fill,
                BackgroundColor = Color.White
            };

            // Нижняя панель для кнопок управления
            Panel bottomPanel = new Panel
            {
                Dock = DockStyle.Bottom,
                Height = 60,
                BackColor = Color.LightGray,
                Padding = new Padding(10)
            };

            // Кнопки управления
            Button btnAdd = new Button { Text = "Добавить", Width = 120, Name = "btnAdd", Location = new Point(10, 10) };
            Button btnEdit = new Button { Text = "Редактировать", Width = 120, Name = "btnEdit", Location = new Point(140, 10) };
            Button btnDelete = new Button { Text = "Удалить", Width = 120, Name = "btnDelete", Location = new Point(270, 10) };

            // Навигация по страницам
            Button btnPrevPage = new Button { Text = "←", Width = 50, Name = "btnPrevPage", Location = new Point(700, 10) };
            Button btnNextPage = new Button { Text = "→", Width = 50, Name = "btnNextPage", Location = new Point(760, 10) };

            // Добавление кнопок на нижнюю панель
            bottomPanel.Controls.Add(btnAdd);
            bottomPanel.Controls.Add(btnEdit);
            bottomPanel.Controls.Add(btnDelete);
            bottomPanel.Controls.Add(btnPrevPage);
            bottomPanel.Controls.Add(btnNextPage);

            // Добавление всех элементов на форму
            this.Controls.Add(dgvProducts);
            this.Controls.Add(topPanel);
            this.Controls.Add(bottomPanel);
        }
    }
}

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
            this.Text = "Список продукции";
            this.Size = new Size(1000, 600);

            // Создание панели для сортировки, фильтрации и поиска
            FlowLayoutPanel controlPanel = new FlowLayoutPanel
            {
                Dock = DockStyle.Top,
                AutoSize = true,
                Padding = new Padding(10),
                FlowDirection = FlowDirection.LeftToRight
            };

            // Метки для сортировки, фильтрации и поиска
            Label lblSort = new Label { Text = "Сортировка:", AutoSize = true };
            Label lblFilter = new Label { Text = "Фильтр:", AutoSize = true };
            Label lblSearch = new Label { Text = "Поиск:", AutoSize = true };

            // Элементы управления
            ComboBox cbSort = new ComboBox
            {
                Width = 150,
                DropDownStyle = ComboBoxStyle.DropDownList,
                Name = "cbSort"
            };
            cbSort.Items.AddRange(new string[] { "Наименование", "Цех", "Минимальная стоимость" });

            ComboBox cbFilter = new ComboBox
            {
                Width = 150,
                DropDownStyle = ComboBoxStyle.DropDownList,
                Name = "cbFilter"
            };
            cbFilter.Items.Add("Все типы");

            TextBox txtSearch = new TextBox
            {
                Width = 200,
                Name = "txtSearch"
            };

            // Добавление элементов на панель
            controlPanel.Controls.Add(lblSort);
            controlPanel.Controls.Add(cbSort);
            controlPanel.Controls.Add(lblFilter);
            controlPanel.Controls.Add(cbFilter);
            controlPanel.Controls.Add(lblSearch);
            controlPanel.Controls.Add(txtSearch);

            // Создание таблицы для отображения списка продукции
            DataGridView dgvProducts = new DataGridView
            {
                Dock = DockStyle.Fill,
                ReadOnly = true,
                MultiSelect = true,
                Name = "dgvProducts",
                AllowUserToAddRows = false,
                AutoSizeColumnsMode = DataGridViewAutoSizeColumnsMode.Fill
            };

            // Панель для кнопок управления
            FlowLayoutPanel buttonPanel = new FlowLayoutPanel
            {
                Dock = DockStyle.Bottom,
                AutoSize = true,
                Padding = new Padding(10)
            };

            Button btnAdd = new Button { Text = "Добавить", Width = 100, Name = "btnAdd" };
            Button btnEdit = new Button { Text = "Редактировать", Width = 100, Name = "btnEdit" };
            Button btnDelete = new Button { Text = "Удалить", Width = 100, Name = "btnDelete" };

            buttonPanel.Controls.Add(btnAdd);
            buttonPanel.Controls.Add(btnEdit);
            buttonPanel.Controls.Add(btnDelete);

            // Панель для навигации по страницам
            FlowLayoutPanel pagePanel = new FlowLayoutPanel
            {
                Dock = DockStyle.Bottom,
                AutoSize = true,
                Padding = new Padding(10)
            };

            Button btnPrevPage = new Button { Text = "←", Width = 50, Name = "btnPrevPage" };
            Button btnNextPage = new Button { Text = "→", Width = 50, Name = "btnNextPage" };

            pagePanel.Controls.Add(btnPrevPage);
            pagePanel.Controls.Add(btnNextPage);

            // Добавление всех элементов на форму
            this.Controls.Add(dgvProducts);
            this.Controls.Add(controlPanel);
            this.Controls.Add(buttonPanel);
            this.Controls.Add(pagePanel);
        }
    }
}

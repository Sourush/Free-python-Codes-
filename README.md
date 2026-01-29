# Free-python-Codes
part 1 : 
This python code look's illegal but its not : 
import pygame
import time
import random

pygame.init()
screen = pygame.display.set_mode((800, 400))
pygame.display.set_caption("ARION HACK SIMULATOR")

font = pygame.font.Font(None, 36)
green = (0, 255, 0)
black = (0, 0, 0)

lines = [
    "Initializing system...",
    "Connecting to server...",
    "Bypassing firewall...",
    "Accessing mainframe...",
    "Decrypting files...",
    "ACCESS GRANTED 🔥"
]

def draw_text(text, y):
    screen.fill(black)
    render = font.render(text, True, green)
    screen.blit(render, (50, y))
    pygame.display.update()

running = True
for line in lines:
    draw_text(line, 180)
    time.sleep(random.uniform(0.8, 1.5))

while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

pygame.quit()

part 2 : 
I made Hacker UI using pygame : 

import pygame
import random
import time
import sys

pygame.init()
WIDTH, HEIGHT = 900, 500
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("ARION :: PRO HACKER UI")

BLACK = (0, 0, 0)
GREEN = (0, 255, 0)
DARK_GREEN = (0, 150, 0)
RED = (255, 0, 0)

font_big = pygame.font.SysFont("consolas", 38)
font = pygame.font.SysFont("consolas", 24)
font_small = pygame.font.SysFont("consolas", 16)

clock = pygame.time.Clock()
class MatrixLine:
    def __init__(self):
        self.x = random.randint(0, WIDTH)
        self.y = random.randint(-HEIGHT, 0)
        self.speed = random.randint(2, 6)
        self.length = random.randint(5, 15)

    def draw(self):
        for i in range(self.length):
            char = random.choice("01#@$%")
            text = font_small.render(char, True, GREEN)
            screen.blit(text, (self.x, self.y - i * 15))
        self.y += self.speed
        if self.y > HEIGHT:
            self.y = random.randint(-100, 0)

matrix_lines = [MatrixLine() for _ in range(40)]
def draw_header():
    title = font_big.render(">>> ARION HACKER SYSTEM <<<", True, GREEN)
    screen.blit(title, (200, 20))

def draw_progress_bar(value):
    pygame.draw.rect(screen, DARK_GREEN, (50, HEIGHT - 60, 800, 20), 2)
    pygame.draw.rect(screen, GREEN, (52, HEIGHT - 58, int(7.96 * value), 16))

def glitch():
    for _ in range(5):
        x = random.randint(0, WIDTH)
        y = random.randint(0, HEIGHT)
        pygame.draw.line(screen, RED, (x, y), (x + 50, y), 1)

def typing(text, y):
    typed = ""
    for char in text:
        typed += char
        screen.fill(BLACK)
        draw_matrix()
        draw_header()
        draw_progress_bar(progress)
        draw_text(typed, y)
        glitch()
        pygame.display.update()
        time.sleep(0.03)

def draw_text(text, y):
    render = font.render(text, True, GREEN)
    screen.blit(render, (50, y))

def draw_matrix():
    for line in matrix_lines:
        line.draw()
def login_screen():
    typing("ENTER USERNAME: Your_name", 120)
    time.sleep(0.5)
    typing("ENTER PASSWORD: ********", 160)
    time.sleep(1)

def password_crack():
    y = 220
    for i in range(1, 101, 5):
        fake_pass = "".join(random.choice("ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789") for _ in range(8))
        screen.fill(BLACK)
        draw_matrix()
        draw_header()
        draw_text("CRACKING PASSWORD...", 120)
        draw_text(f"TRYING KEY: {fake_pass}", 160)
        draw_text(f"PROGRESS: {i}%", y)
        draw_progress_bar(i)
        glitch()
        pygame.display.update()
        time.sleep(0.15)
lines = [
    "Initializing Neural Interface...",
    "Connecting to Secure Server...",
    "Scanning Open Ports...",
    "Injecting Control Protocol...",
    "Decrypting Secure Layers...",
    "Accessing Core Mainframe...",
    "SYSTEM OVERRIDE ENABLED",
]

progress = 0
y_pos = 100

screen.fill(BLACK)
login_screen()
password_crack()
for line in lines:
    typing(line, y_pos)
    y_pos += 40
    progress += 100 // len(lines)
    time.sleep(0.5)
running = True
while running:
    screen.fill(BLACK)
    draw_matrix()
    draw_header()
    draw_progress_bar(100)

    final_text = font_big.render("ACCESS GRANTED :: WELCOME Your_Name", True, GREEN)
    screen.blit(final_text, (180, HEIGHT // 2 - 20))

    exit_text = font_small.render("Press X to Exit | your_name SYSTEM ONLINE", True, GREEN)
    screen.blit(exit_text, (330, HEIGHT // 2 + 30))

    glitch()

    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_x:
                running = False

    pygame.display.update()
    clock.tick(60)

pygame.quit()
sys.exit()


STUDENT MANAGEMENT SYSTEM ( SMALL DATABASE ) . 
import tkinter as tk
from tkinter import messagebox
from tkinter import ttk
class Student:
    def __init__(self, roll_no, name, age, grade):
        self.roll_no = roll_no
        self.name = name
        self.age = age
        self.grade = grade
class StudentManagementSystem:
    def __init__(self):
        self.students = []
        self.load_students()
    def add_student(self, roll_no, name, age, grade):
        student = Student(roll_no, name, age, grade)
        self.students.append(student)
    def update_student(self, roll_no, name=None, age=None, grade=None):
        for student in self.students:
            if student.roll_no == roll_no:
                if name: student.name = name
                if age: student.age = age
                if grade: student.grade = grade
                return True
        return False
    def delete_student(self, roll_no):
        for student in self.students:
            if student.roll_no == roll_no:
                self.students.remove(student)
                return True
        return False
    def get_students(self):
        return [
            f"Roll No: {s.roll_no} | Name: {s.name} | Age: {s.age} | Grade: {s.grade}"
            for s in self.students
        ]
    def save_students(self):
        with open("students_data.txt", "w") as file:
            for s in self.students:
                file.write(f"{s.roll_no},{s.name},{s.age},{s.grade}\n")
    def load_students(self):
        try:
            with open("students_data.txt", "r") as file:
                for line in file:
                    roll_no, name, age, grade = line.strip().split(",")
                    self.students.append(Student(roll_no, name, int(age), grade))
        except FileNotFoundError:
            pass
class StudentApp:
    def __init__(self, root):
        self.root = root
        self.root.title("🎓 Student Management System - By Sourush")
        self.system = StudentManagementSystem()
        self.root.geometry("750x550")
        self.root.configure(bg="#12121c")
        style = ttk.Style()
        style.theme_use("clam")
        style.configure("Accent.TButton",
                        font=("Arial", 12, "bold"),
                        padding=8,
                        relief="flat",
                        background="#2b3a55",   
                        foreground="white")
        style.map("Accent.TButton",
                  background=[("active", "#00d9ff")],
                  foreground=[("active", "black")])
        label_style = {"bg": "#12121c", "fg": "white", "font": ("Arial", 12, "bold")}
        entry_style = {"font": ("Arial", 12),
                       "bg": "#1c1c2b",
                       "fg": "white",
                       "insertbackground": "white",
                       "relief": "flat"}
        self.label_roll_no = tk.Label(root, text="Roll No:", **label_style)
        self.label_roll_no.grid(row=0, column=0, padx=10, pady=5, sticky="w")
        self.entry_roll_no = tk.Entry(root, **entry_style)
        self.entry_roll_no.grid(row=0, column=1, padx=10, pady=5)
        self.label_name = tk.Label(root, text="Name:", **label_style)
        self.label_name.grid(row=1, column=0, padx=10, pady=5, sticky="w")
        self.entry_name = tk.Entry(root, **entry_style)
        self.entry_name.grid(row=1, column=1, padx=10, pady=5)
        self.label_age = tk.Label(root, text="Age:", **label_style)
        self.label_age.grid(row=2, column=0, padx=10, pady=5, sticky="w")
        self.entry_age = tk.Entry(root, **entry_style)
        self.entry_age.grid(row=2, column=1, padx=10, pady=5)
        self.label_grade = tk.Label(root, text="Grade:", **label_style)
        self.label_grade.grid(row=3, column=0, padx=10, pady=5, sticky="w")
        self.entry_grade = tk.Entry(root, **entry_style)
        self.entry_grade.grid(row=3, column=1, padx=10, pady=5)
        self.add_button = ttk.Button(root, text="➕ Add", style="Accent.TButton", command=self.add_student)
        self.add_button.grid(row=4, column=0, padx=10, pady=10)
        self.update_button = ttk.Button(root, text="✏️ Update", style="Accent.TButton", command=self.update_student)
        self.update_button.grid(row=4, column=1, padx=10, pady=10)
        self.delete_button = ttk.Button(root, text="❌ Delete", style="Accent.TButton", command=self.delete_student)
        self.delete_button.grid(row=5, column=0, padx=10, pady=10)
        self.view_button = ttk.Button(root, text="📋 View", style="Accent.TButton", command=self.view_students)
        self.view_button.grid(row=5, column=1, padx=10, pady=10)
        self.save_button = ttk.Button(root, text="💾 Save", style="Accent.TButton", command=self.save_students)
        self.save_button.grid(row=6, column=0, padx=10, pady=10)
        self.output_text = tk.Text(root, height=12, width=50,
                                   font=("Consolas", 12),
                                   bg="#1c1c2b", fg="#00d9ff",
                                   insertbackground="white",
                                   relief="flat")
        self.output_text.grid(row=6, column=1, padx=10, pady=10)
        self.footer_label = tk.Label(root,
                                     text="Made by Sourush ⚡",
                                     bg="#12121c", fg="gray",
                                     font=("Arial", 10, "italic"))
        self.footer_label.grid(row=7, column=0, columnspan=2, pady=5)
    def add_student(self):
        roll_no = self.entry_roll_no.get()
        name = self.entry_name.get()
        age = self.entry_age.get()
        grade = self.entry_grade.get()
        if not roll_no or not name or not age or not grade:
            messagebox.showerror("Input Error", "All fields must be filled!")
            return
        self.system.add_student(roll_no, name, age, grade)
        messagebox.showinfo("Success", "Student added successfully!")
        self.clear_inputs()
    def update_student(self):
        roll_no = self.entry_roll_no.get()
        name = self.entry_name.get()
        age = self.entry_age.get()
        grade = self.entry_grade.get()
        if not roll_no:
            messagebox.showerror("Input Error", "Roll number is required to update!")
            return
        if self.system.update_student(roll_no, name, age, grade):
            messagebox.showinfo("Success", "Student updated successfully!")
        else:
            messagebox.showerror("Error", f"No student found with roll number {roll_no}")
        self.clear_inputs()
    def delete_student(self):
        roll_no = self.entry_roll_no.get()
        if not roll_no:
            messagebox.showerror("Input Error", "Roll number is required to delete!")
            return
        if self.system.delete_student(roll_no):
            messagebox.showinfo("Success", "Student deleted successfully!")
        else:
            messagebox.showerror("Error", f"No student found with roll number {roll_no}")
        self.clear_inputs()
    def view_students(self):
        students = self.system.get_students()
        self.output_text.delete(1.0, tk.END)
        if not students:
            self.output_text.insert(tk.END, "No students available.\n")
        else:
            for student in students:
                self.output_text.insert(tk.END, student + "\n")
    def save_students(self):
        self.system.save_students()
        messagebox.showinfo("Success", "Students saved successfully!")
    def clear_inputs(self):
        self.entry_roll_no.delete(0, tk.END)
        self.entry_name.delete(0, tk.END)
        self.entry_age.delete(0, tk.END)
        self.entry_grade.delete(0, tk.END)
if __name__ == "__main__":
    root = tk.Tk()
    app = StudentApp(root)
    for i in range(8):  
        root.grid_rowconfigure(i, weight=1)
    for j in range(2):
        root.grid_columnconfigure(j, weight=1)
    root.mainloop()

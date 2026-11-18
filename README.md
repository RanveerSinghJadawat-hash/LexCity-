# THE HAUNTED HOTEL - Room 203
# Studio: Your Friendly Neighborhood Studio
# S P I D E R M A N Buttons + Glitch Crash + Hacker Protection
# Voice: Robert = Lohit Sharma, Max = The Wacky Teen, Ghost + ELI = Tu

extends Node3D

@onready var player = $Player
@onready var glitch = $GlitchAnimation
@onready var oom_sound = $OomSound
@onready var crash_msg = $CrashMessage
@onready var hacker_msg = $HackerMessage

var speed = 5.0
var run_speed = 10.0
var gravity = 20.0
var velocity = Vector3.ZERO
var has_gun = false
var current_room = "Room 203"

func _ready():
	print("Game Start - Room 203 - Your Friendly Neighborhood Studio")
	print("S P I D E R M A N Buttons Ready!")
	hacker_msg.hide()
	crash_msg.hide()
	glitch.hide()

func _process(delta):
	# Gravity
	if not player.is_on_floor():
		velocity.y -= gravity * delta
	else:
		velocity.y = 0

	# D = Run - Tez Bhago!
	var move_speed = speed
	if Input.is_action_pressed("D_run"):
		move_speed = run_speed
		print("D = Run!")

	player.move_and_slide()

# S = Jump + Behind Open Door se Bacho!
func _on_S_Button_pressed():
	velocity.y = 8.0
	$DoorBehind.open()
	print("S = Jump + Behind Open Door!")

# P = Door Close - Door Band!
func _on_P_Button_pressed():
	$DoorFront.close()
	print("P = Door Close!")

# I = Door Opens - Door Khulta Hai!
func _on_I_Button_pressed():
	$DoorFront.open()
	print("I = Door Opens! Aage Chalega!")
	# Aage Jayega - Room 204 me!
	# get_tree().change_scene_to_file("res://rooms/room_204.tscn")

# D = Run - Already _process me hai!
func _on_D_Button_pressed():
	print("D = Run!")

# E = Pick Up Items - Cheeze Uthao!
func _on_E_Button_pressed():
	print("E = Pick Up Items! Mizu! Pani!")
	$PickSound.play()

# R = Take Out Gun - Gun Nikalo!
func _on_R_Button_pressed():
	has_gun = true
	$Gun.show()
	print("R = Take Out Gun!")

# M = Open Game Code - Code Kholo!
func _on_M_Button_pressed():
	print("M = Open Game Code!")
	$CodePanel.show()

# A = Leave Game - Game Chodo!
func _on_A_Button_pressed():
	print("A = Leave Game!")
	get_tree().quit()

# N = Open Settings - Settings Kholo!
func _on_N_Button_pressed():
	print("N = Open Settings!")
	$SettingsPanel.show()

# Glitch Crash Animation - Drawing se Banaya!
func play_glitch_crash():
	print("Glitch Crash Animation!")
	glitch.show()
	glitch.play() # Glitch Glitch Glitch!
	oom_sound.play() # Oon Oon Oon!
	crash_msg.text = "GAME CRASHED! Room 203 me Error!"
	crash_msg.show()
	await get_tree().create_timer(2.0).timeout
	crash_msg.hide()
	glitch.hide()
	print("Fake Crash Khatam - Game Wapas!")

# Hacker Protection - Hack hua to!
func _on_Hacker_detected():
	hacker_msg.text = "HACKER DETECTED! A = Leave Game! Report Dabao!"
	hacker_msg.show()
	$ReportButton.show()
	print("Hacker Aaya! Report Karo!")

func _on_ReportButton_pressed():
	print("Report Kar Diya! Hacker Report!")
	hacker_msg.hide()
	$ReportButton.hide()

# Ghost Chase - Prowler Sound!
func _on_Ghost_Chase():
	oom_sound.play() # Oon Oon Oon!
	play_glitch_crash()
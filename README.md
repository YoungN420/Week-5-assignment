# Week-5-assignment

class Robot:
    def __init__(self, name, battery_level):
        self.name = name
        self.__battery_level = battery_level  # Private attribute for encapsulation

    def get_battery_level(self):
        return self.__battery_level

    def set_battery_level(self, level):
        if 0 <= level <= 100:
            self.__battery_level = level
        else:
            print("Invalid battery level! Must be between 0 and 100.")

    def charge(self):
        self.set_battery_level(100)
        print(f"{self.name} is now fully charged! 🔋")

    def work(self):
        if self.get_battery_level() > 0:
            print(f"{self.name} is performing basic tasks...")
            self.set_battery_level(self.get_battery_level() - 10)
        else:
            print(f"{self.name} needs to charge first!")

# Subclass for polymorphism
class CleaningRobot(Robot):
    def work(self):
        if self.get_battery_level() > 0:
            print(f"{self.name} is vacuuming the floor with laser precision! 🤖🧹")
            self.set_battery_level(self.get_battery_level() - 15)
        else:
            print(f"{self.name} needs to charge first!")

# Another subclass for polymorphism
class CookingRobot(Robot):
    def work(self):
        if self.get_battery_level() > 0:
            print(f"{self.name} is whipping up a gourmet algorithm-inspired meal! 🤖🍲")
            self.set_battery_level(self.get_battery_level() - 20)
        else:
            print(f"{self.name} needs to charge first!")

# Creating objects with unique initial values
clean_bot = CleaningRobot("SparkleBot 3000", 60)  # Unique name and starting battery
chef_bot = CookingRobot("FlavorMaster AI", 85)     # Different unique values

# Demonstrating encapsulation and methods
print(f"Initial battery for {clean_bot.name}: {clean_bot.get_battery_level()}%")
clean_bot.work()  # Polymorphic behavior
clean_bot.charge()  # Shared method
clean_bot.work()   # After charging

print(f"\nInitial battery for {chef_bot.name}: {chef_bot.get_battery_level()}%")
chef_bot.work()    # Different polymorphic behavior
chef_bot.charge()
chef_bot.work()

# Showing polymorphism in a loop
robots = [clean_bot, chef_bot]
print("\nAll robots in action:")
for robot in robots:
    robot.work()

class BucketList:
    def __init__(self):
        self.goals = []

    def add_goal(self, goal):
        self.goals.append(goal)
        print("Goal Added!")

    def remove_goal(self, goal):
        if goal in self.goals:
            self.goals.remove(goal)
            print("Goal Removed!")
        else:
            print("Goal not found!")

    def display_goals(self):
        print("\nMy Bucket List:")
        for i, goal in enumerate(self.goals, start=1):
            print(f"{i}. {goal}")


bucket = BucketList()

bucket.add_goal("Visit Japan")
bucket.add_goal("Learn Python")
bucket.add_goal("Build a Mobile App")

bucket.display_goals()

bucket.remove_goal("Learn Python")

bucket.display_goals()
